--"C:\Users\000356\source\repos\AFOS\dbscript\field_option.sql"  
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
SELECT @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
SELECT @owfield = 1, @owoption = 1; 
  
--更新欄位選項及說明 
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

INSERT #appTableFieldo SELECT 2, '2.交易型態', 1;
INSERT #appTableFieldoi SELECT 2, 1, 'B', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 2, 2, 'S', @loguser, @dt; 

INSERT #appTableFieldo SELECT 3, '3.Asset Or Liability', 1;
INSERT #appTableFieldoi SELECT 3, 1, 'A', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 3, 2, 'L', @loguser, @dt; 

INSERT #appTableFieldo SELECT 4, '4.Date Type', 1;
INSERT #appTableFieldoi SELECT 4, 1, '1.Holiday', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 4, 2, '2.Working Day', @loguser, @dt; 

INSERT #appTableFieldo SELECT 5, '5.MM Product', 1;
INSERT #appTableFieldoi SELECT 5, 1, 'DEP', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 5, 2, 'MML', @loguser, @dt; 

INSERT #appTableFieldo SELECT 7, '7.Broker Code', 1;
INSERT #appTableFieldoi SELECT 7, 1, '1.BFC', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 7, 2, '2.BVA', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 7, 3, '3.CDR', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 7, 4, '4.CED', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 7, 5, '5.COS', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 7, 6, '6.FOR', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 7, 7, '7.FTS', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 7, 8, '8.ITD', @loguser, @dt;
INSERT #appTableFieldoi SELECT 7, 9, '9.P', @loguser, @dt; 

INSERT #appTableFieldo SELECT 8, '8.Product Type', 1;
INSERT #appTableFieldoi SELECT 8, 1, '1.Unwind', @loguser, @dt;
INSERT #appTableFieldoi SELECT 8, 2, '2.Rollover', @loguser, @dt;
INSERT #appTableFieldoi SELECT 8, 3, '3.Fixing', @loguser, @dt;

INSERT #appTableFieldo SELECT 9, '9.Matching Type', 1;
INSERT #appTableFieldoi SELECT 9, 1, '1.Matched By AFOS', @loguser, @dt;
INSERT #appTableFieldoi SELECT 9, 2, '2.Matched By User', @loguser, @dt;

INSERT #appTableFieldo SELECT 27, '27.Calculated Type', 1;
INSERT #appTableFieldoi SELECT 27, 1, '1.R', @loguser, @dt;
INSERT #appTableFieldoi SELECT 27, 2, '2.M', @loguser, @dt;

INSERT #appTableFieldo SELECT 29, '29.Holiday Type', 1;
INSERT #appTableFieldoi SELECT 29, 1, 'Saturday, Sunday', @loguser, @dt;
INSERT #appTableFieldoi SELECT 29, 2, 'Friday, Saturday', @loguser, @dt;

INSERT #appTableFieldo SELECT 33, '33.Broker Type', 1;
INSERT #appTableFieldoi SELECT 33, 1, '1.共用中心', @loguser, @dt;
INSERT #appTableFieldoi SELECT 33, 2, '2.央行或本國銀行', @loguser, @dt;
INSERT #appTableFieldoi SELECT 33, 3, '3.信用合作社', @loguser, @dt;
INSERT #appTableFieldoi SELECT 33, 4, '4.漁會', @loguser, @dt;
INSERT #appTableFieldoi SELECT 33, 5, '5.農會', @loguser, @dt;
INSERT #appTableFieldoi SELECT 33, 6, '6.外商單位', @loguser, @dt;
INSERT #appTableFieldoi SELECT 33, 7, '7.其他單位', @loguser, @dt;
INSERT #appTableFieldoi SELECT 33, 8, '8.郵局', @loguser, @dt;

INSERT #appTableFieldo SELECT 73, '73.交易型態', 1;
INSERT #appTableFieldoi SELECT 73, 1, '1.Spot(FXC)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 73, 2, '2.Forward(FXF)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 73, 3, '3.SWAP(FXS)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 73, 4, '4.NDF(FXFN)', @loguser, @dt;

INSERT #appTableFieldo SELECT 75, '75.SWAP S/F', 1;
INSERT #appTableFieldoi SELECT 75, 1, '1.Spot Leg', @loguser, @dt;
INSERT #appTableFieldoi SELECT 75, 2, '2.Forward Leg', @loguser, @dt;

INSERT #appTableFieldo SELECT 100, '100.資料轉換方式', 1; 
INSERT #appTableFieldoi SELECT 100, 1, '1.CSV', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 100, 2, '2.Excel', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 100, 3, '3.TXT', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 100, 4, '4.MSSQL', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 100, 5, '5.ORACLE', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 100, 6, '6.External Files', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 100, 9, '9. Other', @loguser, @dt; 

INSERT #appTableFieldo SELECT 101, '101.資料庫類型', 1; 
INSERT #appTableFieldoi SELECT 101, 0, '0.MSSQL', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 101, 1, '1.ORACLE', @loguser, @dt;

INSERT #appTableFieldo SELECT 102, '102.重覆資料處理方式', 1; 
INSERT #appTableFieldoi SELECT 102, 0, 'None', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 102, 1, '1.All', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 102, 2, '2.ByKey', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 102, 3, '3.ByDate', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 102, 4, '4.ByDef', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 102, 5, '5.Update', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 102, 6, '6.New', @loguser, @dt;
INSERT #appTableFieldoi SELECT 102, 7, '7.Year', @loguser, @dt;
INSERT #appTableFieldoi SELECT 102, 8, '8.YearMonth', @loguser, @dt;

INSERT #appTableFieldo SELECT 103, '103.資料轉換方式', 1; 
INSERT #appTableFieldoi SELECT 103, 0, '不處理', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 103, 1, '系統時間', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 103, 2, '西元年(YYYY/MM/DD)', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 103, 3, '西元年(DD/MM/YYYY)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 103, 4, '西元年(MM/DD/YYYY)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 103, 5, '民國年(YYYMMDD)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 103, 6, 'EXCEL日期', @loguser, @dt;
INSERT #appTableFieldoi SELECT 103, 7, '執行日期', @loguser, @dt;
--INSERT #appTableFieldoi SELECT 103, 8, '移除結尾空白', @loguser, @dt;
--INSERT #appTableFieldoi SELECT 103, 9, '變大寫', @loguser, @dt;
--INSERT #appTableFieldoi SELECT 103, 10, '變小寫', @loguser, @dt;
INSERT #appTableFieldoi SELECT 103, 11, '西元年(YYYYMMDD)', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 103, 12, '民國年(YYY/MM/DD)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 103, 99, '系統使用者', @loguser, @dt; 

INSERT #appTableFieldo SELECT 104, '104.ETL作業型態', 1; 
INSERT #appTableFieldoi SELECT 104, 1, '匯入資料庫', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 104, 2, '匯出檔案', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 104, 3, '匯出報表', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 104, 4, '執行預儲程序', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 104, 5, '外部執行檔', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 104, 6, 'SQL語法', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 104, 7, '傳送檔案', @loguser, @dt; 
--INSERT #appTableFieldoi SELECT 104, 8, 'SNX轉檔', @loguser, @dt;

INSERT #appTableFieldo SELECT 105, '105.轉碼型態', 1; 
INSERT #appTableFieldoi SELECT 105, 1, '1.手動建立', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 105, 2, '2.系統資料表', @loguser, @dt; 

INSERT #appTableFieldo SELECT 106, '106.資料異動方式', 1; 
INSERT #appTableFieldoi SELECT 106, 0, '不異動', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 106, 1, '異動時為KEY值', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 106, 2, '異動', @loguser, @dt; 

INSERT #appTableFieldo SELECT 107, '107.作業日期定義', 1; 
INSERT #appTableFieldoi SELECT 107, -1, 'N/A', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 107, 0, '執行日', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 107, 1, '執行日前日', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 107, 2, '執行日上月月底', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 107, 3, '執行日上月月初', @loguser, @dt;
INSERT #appTableFieldoi SELECT 107, 4, '執行日本月月初', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 107, 5, '執行日前二日', @loguser, @dt;
INSERT #appTableFieldoi SELECT 107, 6, '執行日前三日', @loguser, @dt;
INSERT #appTableFieldoi SELECT 107, 7, '執行日前四日', @loguser, @dt;
INSERT #appTableFieldoi SELECT 107, 8, '執行日前五日', @loguser, @dt;

INSERT #appTableFieldo SELECT 108, '108.主鍵處理方式', 1; 
INSERT #appTableFieldoi SELECT 108, 0, '不處理', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 108, 1, '流水號(INT)主鍵', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 108, 11, '股票內碼', @loguser, @dt;
INSERT #appTableFieldoi SELECT 108, 12, '債券內碼', @loguser, @dt;
INSERT #appTableFieldoi SELECT 108, 13, '基金內碼', @loguser, @dt;
INSERT #appTableFieldoi SELECT 108, 14, '境外結構型商品內碼', @loguser, @dt;
INSERT #appTableFieldoi SELECT 108, 15, 'Pgn內碼', @loguser, @dt;

INSERT #appTableFieldo SELECT 109, '109. Fax Protocol Type', 1; 
INSERT #appTableFieldoi SELECT 109, 1, 'Named Pipes', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 109, 2, 'IPXOS2', @loguser, @dt;
INSERT #appTableFieldoi SELECT 109, 3, 'SPX', @loguser, @dt;
INSERT #appTableFieldoi SELECT 109, 4, 'TCPIP', @loguser, @dt;
INSERT #appTableFieldoi SELECT 109, 5, 'IPX', @loguser, @dt;
INSERT #appTableFieldoi SELECT 109, 6, 'SecTCPIP', @loguser, @dt;
INSERT #appTableFieldoi SELECT 109, 7, 'SecSpx', @loguser, @dt;

INSERT #appTableFieldo SELECT 110, '110.排程執行週期', 1;
INSERT #appTableFieldoi SELECT 110, 1, '1.每日', @loguser, @dt;
INSERT #appTableFieldoi SELECT 110, 2, '2.每週', @loguser, @dt;
INSERT #appTableFieldoi SELECT 110, 3, '3.每月', @loguser, @dt;

INSERT #appTableFieldo SELECT 111, '111.execdatetp', 1;
INSERT #appTableFieldoi SELECT 111, 1, '1.當日', @loguser, @dt;
INSERT #appTableFieldoi SELECT 111, 2, '2.前日', @loguser, @dt;
INSERT #appTableFieldoi SELECT 111, 3, '3.前月月底', @loguser, @dt;

INSERT #appTableFieldo SELECT 112, '112.執行程式類型', 1;
INSERT #appTableFieldoi SELECT 112, 1, '1.預儲程序', @loguser, @dt;
INSERT #appTableFieldoi SELECT 112, 2, '2.外部執行檔', @loguser, @dt;
INSERT #appTableFieldoi SELECT 112, 3, '3.SQL語法', @loguser, @dt;

INSERT #appTableFieldo SELECT 114, '114.Confirmation Type', 1;
INSERT #appTableFieldoi SELECT 114, 1, '1.Short Form', @loguser, @dt;
INSERT #appTableFieldoi SELECT 114, 2, '2.NDF LF', @loguser, @dt;
INSERT #appTableFieldoi SELECT 114, 3, '3.NDF Non Std LF', @loguser, @dt;
INSERT #appTableFieldoi SELECT 114, 4, '4.Short Form(For IM)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 114, 5, '5.Short Form(For Custodian)', @loguser, @dt;

INSERT #appTableFieldo SELECT 116, '116.匯率報價', 1;
INSERT #appTableFieldoi SELECT 116, 1, '1.匯率報價(分子)', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 116, 2, '2.基礎幣別(分母)', @loguser, @dt; 

INSERT #appTableFieldo SELECT 121, '121.檢查代碼', 1;
INSERT #appTableFieldoi SELECT 121, 0, '0.不檢查log，不製作rpt', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 121, 1, '1.檢查log，製作rpt', @loguser, @dt; 

INSERT #appTableFieldo SELECT 165, '165.換匯作業項目', 1;
INSERT #appTableFieldoi SELECT 165, 1, '1.付款方式/匯款方式', @loguser, @dt;
INSERT #appTableFieldoi SELECT 165, 2, '2.單據別', @loguser, @dt;
INSERT #appTableFieldoi SELECT 165, 3, '3.交易日報類別', @loguser, @dt;
INSERT #appTableFieldoi SELECT 165, 4, '4.匯入(出)匯款分類', @loguser, @dt;
INSERT #appTableFieldoi SELECT 165, 5, '5.交易性質註記', @loguser, @dt;
INSERT #appTableFieldoi SELECT 165, 6, '6.匯(受)款人身分別', @loguser, @dt;
INSERT #appTableFieldoi SELECT 165, 7, '7.有無申報書別', @loguser, @dt;
INSERT #appTableFieldoi SELECT 165, 8, '8.結售/結匯外匯性質別', @loguser, @dt;
INSERT #appTableFieldoi SELECT 165, 9, '9.結匯人身分別', @loguser, @dt;

INSERT #appTableFieldo SELECT 501, '501.Counterparty Type', 1; /* afos_client_chop.cp_type */
INSERT #appTableFieldoi SELECT 501, 1, '1.CORP', @loguser, @dt;
INSERT #appTableFieldoi SELECT 501, 2, '2.FUND', @loguser, @dt;
INSERT #appTableFieldoi SELECT 501, 3, '3.IM', @loguser, @dt;
INSERT #appTableFieldoi SELECT 501, 4, '4.BANK', @loguser, @dt;
INSERT #appTableFieldoi SELECT 501, 5, '5.BKIN', @loguser, @dt;
INSERT #appTableFieldoi SELECT 501, 6, '6.BROKER', @loguser, @dt;

INSERT #appTableFieldo SELECT 502, '502.Fund Type', 1; /* afos_client_chop.fund_type */
INSERT #appTableFieldoi SELECT 502, 1, '1.Custody', @loguser, @dt;
INSERT #appTableFieldoi SELECT 502, 2, '2.3rd party', @loguser, @dt;

INSERT #appTableFieldo SELECT 503, '503.Fund Location Type', 1; /* afos_client_chop.fund_location_type */
INSERT #appTableFieldoi SELECT 503, 1, '1.Onshore', @loguser, @dt;
INSERT #appTableFieldoi SELECT 503, 2, '2.Offshore', @loguser, @dt;

INSERT #appTableFieldo SELECT 504, '504.File Type', 1; /* afos_client_chop.type */
INSERT #appTableFieldoi SELECT 504, 1, '1.Sign', @loguser, @dt;
INSERT #appTableFieldoi SELECT 504, 2, '2.Chop', @loguser, @dt;

INSERT #appTableFieldo SELECT 505, '505.Contact Type', 1; /* afos_client_contact.contact_type */
INSERT #appTableFieldoi SELECT 505, 1, '1.FO', @loguser, @dt;
INSERT #appTableFieldoi SELECT 505, 2, '2.BO', @loguser, @dt;
INSERT #appTableFieldoi SELECT 505, 3, '3.Accounting', @loguser, @dt;
INSERT #appTableFieldoi SELECT 505, 4, '4.Declaration Form', @loguser, @dt;
INSERT #appTableFieldoi SELECT 505, 5, '5.Master Custodian', @loguser, @dt;
INSERT #appTableFieldoi SELECT 505, 6, '6.Sub Custodian', @loguser, @dt;
INSERT #appTableFieldoi SELECT 505, 7, '7.MM', @loguser, @dt;

INSERT #appTableFieldo SELECT 506, '506.OTC Counterparty Type', 1; /* afos_client_local.otc_cp_type */
INSERT #appTableFieldoi SELECT 506,  1,  '1.國內金融機構（限銀行、票券、證券、保險、期貨）', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506,  2,  '2.國內政府機構(含政府基金)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506,  3,  '3.國內其他法人', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506,  4,  '4.國內個人', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506,  5,  '5.國外金融機構', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506,  6,  '6.國外法人、個人', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506,  7,  '7.國內金融機構海外分公司', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506,  8,  '8.去識別化-對手未同意', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506,  9,  '9.去識別化-當地國法令', @loguser, @dt;
INSERT #appTableFieldoi SELECT 506, 10, '10.CCP', @loguser, @dt;

INSERT #appTableFieldo SELECT 507, '507.OTC Counterparty', 1; /* afos_client_local.oct_cp_entity_type */
INSERT #appTableFieldoi SELECT 507,  1,  '1.一般客戶', @loguser, @dt;
INSERT #appTableFieldoi SELECT 507,  2,  '2.專業客戶', @loguser, @dt;
INSERT #appTableFieldoi SELECT 507,  3,  '3.專業機構投資人', @loguser, @dt;

INSERT #appTableFieldo SELECT 508, '508.Trade Confirmation Submit Type', 1; /* afos_client_local.cfm_submit_type */
INSERT #appTableFieldoi SELECT 508,  1,  '1.MT300', @loguser, @dt;
INSERT #appTableFieldoi SELECT 508,  2,  '2.Email', @loguser, @dt;
INSERT #appTableFieldoi SELECT 508,  3,  '3.Fax', @loguser, @dt;
INSERT #appTableFieldoi SELECT 508,  4,  '4.Both Email And Fax', @loguser, @dt;

INSERT #appTableFieldo SELECT 509, '509.Trade Confirmation Receive Type', 1; /* afos_client_local.cfm_rec_type */
INSERT #appTableFieldoi SELECT 509,  1,  '1.MT300', @loguser, @dt;
INSERT #appTableFieldoi SELECT 509,  2,  '2.Email', @loguser, @dt;
INSERT #appTableFieldoi SELECT 509,  3,  '3.Fax', @loguser, @dt;

INSERT #appTableFieldo SELECT 510, '510.Trade Confirmation Check Type', 1; /* afos_client_local.cfm_chk_type */
INSERT #appTableFieldoi SELECT 510,  1,  '1.Not Required', @loguser, @dt;
INSERT #appTableFieldoi SELECT 510,  2,  '2.Received But Reconciliation Is Not Required', @loguser, @dt;
INSERT #appTableFieldoi SELECT 510,  3,  '3.Received Reconciliation Is Required', @loguser, @dt;

INSERT #appTableFieldo SELECT 511, '511.Status', 1; /* afos_client_local.status */
INSERT #appTableFieldoi SELECT 511,  1,  '1.Pending', @loguser, @dt;
INSERT #appTableFieldoi SELECT 511,  2,  '2.Active', @loguser, @dt;
INSERT #appTableFieldoi SELECT 511,  3,  '3.Closed', @loguser, @dt;

INSERT #appTableFieldo SELECT 512, '512.Modifying Status', 1; /* afos_client_local.mod_status */
INSERT #appTableFieldoi SELECT 512,  1,  '1.Modifying', @loguser, @dt;
INSERT #appTableFieldoi SELECT 512,  2,  '2.Waiting For Approval(Active)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 512,  3,  '3.Waiting For Approval(Modifying)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 512,  4,  '4.Waiting For Approval(Close)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 512,  5,  '5.Waiting For Approval(Delete)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 512,  6,  '6.Confirmed', @loguser, @dt;

INSERT #appTableFieldo SELECT 513, '513.Remit Type', 1; /* afos_client_remit_class.trade_type */
INSERT #appTableFieldoi SELECT 513,  1,  '1.Inward', @loguser, @dt;
INSERT #appTableFieldoi SELECT 513,  2,  '2.Outward', @loguser, @dt;

INSERT #appTableFieldo SELECT 514, '514.Recevied Confirmation Status', 1; /* cfm_received_record.cfm.cfm_status */
INSERT #appTableFieldoi SELECT 514,  1,  '1.Pending', @loguser, @dt;
INSERT #appTableFieldoi SELECT 514,  2,  '2.Verified', @loguser, @dt;
INSERT #appTableFieldoi SELECT 514,  3,  '3.Rejected', @loguser, @dt;

INSERT #appTableFieldo SELECT 515, '515.Trade Confirmation Status', 1; /* cfm_delivered_record_fx.status */
INSERT #appTableFieldoi SELECT 515,  1,  '1.Success', @loguser, @dt;
INSERT #appTableFieldoi SELECT 515,  2,  '2.Pending', @loguser, @dt;
INSERT #appTableFieldoi SELECT 515,  3,  '3.Rejected', @loguser, @dt;

INSERT #appTableFieldo SELECT 516, '516.Confirmed Type', 1; /*cfm_confirmed_record.cfm_type */
INSERT #appTableFieldoi SELECT 516, 1, '1.Default Confirmed', @loguser, @dt;
INSERT #appTableFieldoi SELECT 516, 2, '2.Confirmed When Received', @loguser, @dt;
INSERT #appTableFieldoi SELECT 516, 3, '3.Confirmed By Manual Release', @loguser, @dt;
INSERT #appTableFieldoi SELECT 516, 4, '4.Confirmed By Chop/Sign', @loguser, @dt;

INSERT #appTableFieldo SELECT 901, '901.數值型態', 1;
INSERT #appTableFieldoi SELECT 901, 0, '0.未設定', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 1, '1.金額', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 2, '2.股票價格', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 3, '3.債券價格', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 4, '4.利率', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 5, '5.淨值', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 6, '6.單位數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 7, '7.匯率', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 8, '8.比例', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 9, '9.數量', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 10, '10.固定0位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 11, '11.固定1位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 12, '12.固定2位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 13, '13.固定3位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 14, '14.固定4位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 15, '15.固定5位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 16, '16.固定6位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 17, '17.固定7位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 18, '18.固定8位小數', @loguser, @dt;
INSERT #appTableFieldoi SELECT 901, 19, '19.固定9位小數', @loguser, @dt;

INSERT #appTableFieldo SELECT 902, '902.大小寫型態', 1;
INSERT #appTableFieldoi SELECT 902, 0, '0.未設定', @loguser, @dt;
INSERT #appTableFieldoi SELECT 902, 1, '1.全部大寫', @loguser, @dt;
INSERT #appTableFieldoi SELECT 902, 2, '2.全部小寫', @loguser, @dt;

INSERT #appTableFieldo SELECT 903, '903.Log Result', 1;
INSERT #appTableFieldoi SELECT 903, 1, '1.Successful', @loguser, @dt;
INSERT #appTableFieldoi SELECT 903, 2, '2.Deactivated', @loguser, @dt;
INSERT #appTableFieldoi SELECT 903, 3, '3.Account Not Exist', @loguser, @dt;
/*
INSERT #appTableFieldoi SELECT 903, 5, '5.Syster password error', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 903, 6, '6.User ID is empty', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 903, 7, '7.User is locked', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 903, 8, '8.Password Expired', @loguser, @dt;
INSERT #appTableFieldoi SELECT 903, 9, '9.AD password error', @loguser, @dt; 
*/

INSERT #appTableFieldo SELECT 904, '904.User Status', 1;
INSERT #appTableFieldoi SELECT 904, 1, '1.Deactivated', @loguser, @dt;
INSERT #appTableFieldoi SELECT 904, 2, '2.Activated', @loguser, @dt;
INSERT #appTableFieldoi SELECT 904, 3, '3.New', @loguser, @dt;
INSERT #appTableFieldoi SELECT 904, 4, '4.Deleted', @loguser, @dt;

INSERT #appTableFieldo SELECT 905, '905.Execute Type', 1;
INSERT #appTableFieldoi SELECT 905, 1, '1.Manual', @loguser, @dt;
INSERT #appTableFieldoi SELECT 905, 2, '2.Auto', @loguser, @dt

INSERT #appTableFieldo SELECT 10001, '10001.匯出日期設定', 1;
INSERT #appTableFieldoi SELECT 10001, 0, '不處理', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10001, 2, '西元年(YYYY/MM/DD)', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10001, 3, '西元年(DD/MM/YYYY)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10001, 4, '西元年(MM/DD/YYYY)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10001, 5, '民國年(YYYMMDD)', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10001, 11, '西元年(YYYYMMDD)', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10001, 12, '民國年(YYY/MM/DD)', @loguser, @dt;

INSERT #appTableFieldo SELECT 10002, '10002.匯出檔欄位型態', 1; 
INSERT #appTableFieldoi SELECT 10002, 1, '文字', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10002, 2, '數字', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10002, 3, '日期', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10002, 4, '自定義', @loguser, @dt;

INSERT #appTableFieldo SELECT 10003, '10003.檢核類型', 1;
INSERT #appTableFieldoi SELECT 10003, 0, '0.無', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10003, 1, '1.總筆數', @loguser, @dt;

INSERT #appTableFieldo SELECT 10004, '10004.外送檔案類型', 1;
INSERT #appTableFieldoi SELECT 10004, 1, '1.匯出檔案', @loguser, @dt;
--INSERT #appTableFieldoi SELECT 10004, 2, '2.匯出報表', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10004, 9, '9.靜態檔案', @loguser, @dt;

INSERT #appTableFieldo SELECT 10005, '10005.匯入檔案來源', 1;
--INSERT #appTableFieldoi SELECT 10005, 1, '1.EMail', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10005, 2, '2.FTP', @loguser, @dt;

INSERT #appTableFieldo SELECT 10006, '10006.匯出檔案格式', 1; 
INSERT #appTableFieldoi SELECT 10006, 1, '1.CSV', @loguser, @dt; 
--INSERT #appTableFieldoi SELECT 10006, 2, '2.Excel', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10006, 3, '3.TXT', @loguser, @dt; 

INSERT #appTableFieldo SELECT 10007, '10007.匯入檔案資料格式', 1; 
INSERT #appTableFieldoi SELECT 10007, 1, '1.CSV', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10007, 2, '2.Excel', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10007, 3, '3.TXT', @loguser, @dt; 

INSERT #appTableFieldo SELECT 10008, '10008.匯出編碼格式', 1; 
INSERT #appTableFieldoi SELECT 10008, 1, 'BIG5', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10008, 2, 'UTF8', @loguser, @dt; 

INSERT #appTableFieldo SELECT 10009, '10009.控制項設定', 1
INSERT #appTableFieldoi SELECT 10009, 1, '1.契約', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10009, 2, '2.日期', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10009, 3, '3.自訂值', @loguser, @dt;

INSERT #appTableFieldo SELECT 10010, '10010.自訂值型態', 1
INSERT #appTableFieldoi SELECT 10010, 1, '1.String', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10010, 2, '2.Int', @loguser, @dt;
INSERT #appTableFieldoi SELECT 10010, 3, '3.Decimal', @loguser, @dt; 
INSERT #appTableFieldoi SELECT 10010, 4, '4.Datetime', @loguser, @dt;

IF @owoption=1 
BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
        WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
        WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
END;  
DROP TABLE #appTableFieldo, #appTableFieldoi; 


IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\insert_app_option.sql"  
DELETE app_option WHERE opt_name = 'user_deletion_date_period'
INSERT app_option VALUES ('user_deletion_date_period','120','沒登入刪除帳號週期')

DELETE app_option WHERE opt_name = 'user_deactivated_date_period'
INSERT app_option VALUES ('user_deactivated_date_period', '60', '沒登入停止帳號週期')

DELETE app_option WHERE opt_name = 'WindowsIdentityAsLoginID'
INSERT app_option VALUES ('WindowsIdentityAsLoginID', 'True', '使用 Microsoft AD提供的 User ID做為帳號')

DELETE app_option WHERE opt_name = 'Verification Station'
INSERT app_option VALUES ('Verification Station', 'C:\ProgramData\Microsoft\Windows\Start Menu\Programs\ABBYY FlexiCapture 11\Verification Station.lnk', 'FlexiCapture 11 Verification Station在Citrix Server上的路徑')

DELETE app_option WHERE opt_name = 'Data Verification Station'
INSERT app_option VALUES ('Data Verification Station', 'C:\ProgramData\Microsoft\Windows\Start Menu\Programs\ABBYY FlexiCapture 11\Data Verification Station.lnk', 'FlexiCapture 11 Data Verification Station在Citrix Server上的路徑')

DELETE app_option WHERE opt_name = 'board_refresh_interval'
INSERT app_option VALUES ('board_refresh_interval',	'600000'	,'佈告欄定期更新時間(單位:毫秒)')

DELETE app_option WHERE opt_name = 'heartbeat_interval'
INSERT app_option VALUES ('heartbeat_interval',	'30000'	,'單位:毫秒')

DELETE app_option WHERE opt_name = 'try_connect'
INSERT app_option VALUES ('try_connect',	'3'	,'單位:次')

DELETE app_option WHERE opt_name = 'RecordButton'
INSERT app_option VALUES ('RecordButton',	'True'	,'')

DELETE app_option WHERE opt_name = 'RecordSql'
INSERT app_option VALUES ('RecordSql',	'True'	,'')

DELETE app_option WHERE opt_name = 'sys_company_cname'
INSERT app_option VALUES ('sys_company_cname',	'美商道富銀行'	,'客戶公司中文名稱')

DELETE app_option WHERE opt_name = 'sys_name'
INSERT app_option VALUES ('sys_name',	'AFOS'	,'系統名稱')


DELETE app_option WHERE opt_name = 'cfm_file_path'
INSERT app_option VALUES ('cfm_file_path',	'D:\AFOS_FILE\'	,'交易確認文件絕對路徑')

DELETE app_option WHERE opt_name = 'AutoLogin'
INSERT app_option VALUES ('AutoLogin',	'False'	,'是否自動登入')

DELETE app_option WHERE opt_name = 'CB_BANK_FAGN'
INSERT app_option VALUES ('CB_BANK_FAGN',	'FAGN'	,'FAGN字軌')

DELETE app_option WHERE opt_name = 'SSB_SWIFT_CODE'
INSERT app_option VALUES ('SSB_SWIFT_CODE',	'SBOSTWTP'	,'SSB SWIFT CODE')


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetCalendar.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetCalendar') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetCalendar;
GO

/*---------------------------------
版本 : 1.0.0
日期 : 2016-08-19
內容 : 回傳年度的日期、星期、是否工作天
---------------------------------*/
CREATE FUNCTION [dbo].[fn_GetCalendar]
	(@input_date DATE, @calendar_target VARCHAR(10), @calendar_catalog INT,@offset_year INT)

 RETURNS @calendar TABLE([date_to_work] DATE, [day_week] INT, is_working_date BIT)
AS
BEGIN

-- var
DECLARE @target VARCHAR(10)
DECLARE @holiday_dayweek TABLE (dayweek INT NOT NULL)


-- check country and is_holiday_for_ss
IF (@calendar_catalog =1)
BEGIN
	SELECT @target = ccy FROM cmn_currency WHERE ccy = @calendar_target
	SET @target = ISNULL(@target,@calendar_target)
END
ELSE
BEGIN
	SELECT TOP(1) @target = market FROM cmn_market WHERE country = @calendar_target ORDER BY country DESC
	SET @target = ISNULL(@target, @calendar_target)
END

--如果有宣告 @is_holiday_for_SS，查詢成本上升
--DECLARE @is_holiday_for_SS BIT = (SELECT CASE WHEN holiday_type = 1 THEN 1 ELSE 0 END from cmn_country WHERE country = @country)
--IF(@is_holiday_for_SS =1)
DECLARE @holiday_type INT = 0
SELECT @holiday_type = holiday_type FROM cmn_currency WHERE ccy = @target

IF(@holiday_type = 1)
	INSERT into @holiday_dayweek VALUES(6),(0)
ELSE IF(@holiday_type = 2)
	INSERT into @holiday_dayweek VALUES(5),(6)
ELSE
BEGIN
	INSERT into @holiday_dayweek VALUES(1),(2),(3),(4),(5),(6),(0)
END

-- Get specific cmn_calendar_setting
DECLARE @temp_setting_table TABLE([date] DATE,[date_type] SMALLINT)
--修改table後，應為 WHERE target = @calendar_target
--INSERT into @temp_setting_table ([date], [type]) (SELECT [date], [type] FROM cmn_calendar_setting WHERE market = @calendar_target )--AND [type] = @type)
INSERT into @temp_setting_table ([date], [date_type]) (SELECT [date], [date_type] FROM cmn_calendar_setting WHERE [target] = @target AND calendar_catalog = @calendar_catalog)
--select* from @temp_setting_table

DECLARE @date_from DATE = DATEFROMPARTS(YEAR(@input_date) - @offset_year,1,1)
DECLARE @date_to DATE = DATEADD(day,-1, DATEFROMPARTS(YEAR(@input_date) +1 + @offset_year,1,1))

;WITH CTE AS
(
	SELECT @date_from AS [date_to_work]
	UNION ALL
	SELECT DATEADD(dd,1,[date_to_work])
	FROM CTE
	WHERE [date_to_work] < @date_to
)
INSERT INTO @calendar ([date_to_work],[day_week],[is_working_date]) SELECT [date_to_work] , (DATEPART(WEEKDAY, [date_to_work])+ @@DATEFIRST -1)%7 AS dw --,ROW_NUMBER() OVER( ORDER BY [date_to_work] ASC ) AS ROW#
, ISNULL(CASE WHEN TEMP.[date_type] = 2 THEN 1
				WHEN TEMP.[date_type] =1 THEN 0 END,
			CASE 
				WHEN (DATEPART(WEEKDAY, [date_to_work])+ @@DATEFIRST -1)%7 not in (SELECT dayweek FROM @holiday_dayweek)
				THEN 1 
				ELSE 0 
			END
		) AS is_working_date
FROM CTE AS CTE
LEFT JOIN @temp_setting_table AS TEMP ON CTE.date_to_work = TEMP.[date]
OPTION (MAXRECURSION 0)

RETURN

END
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetClientChopSign.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetClientChopSign') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetClientChopSign;
GO

/*---------------------------------
版本 : 1.0.0
日期 : 2017-11-22
內容 : 輸入lno取得指定日期下最新的印鑑或簽章檔案

---------------------------------*/
CREATE FUNCTION fn_GetClientChopSign (@lno INT, @date DATE)
 RETURNS @result TABLE(lno INT, object VARBINARY(MAX))
AS
BEGIN
		IF(@date = '')
			SELECT @date = CAST(GETDATE() AS DATE)

		DECLARE @temp TABLE(lno INT, object VARBINARY(MAX), date DATE)

		DECLARE @lno_im		INT = 0

		SELECT @lno_im = ISNULL(lno, 0)
		  FROM vw_contract AS v
		 WHERE pno IN (SELECT pno_im FROM vw_contract WHERE lno = @lno)

		IF(@lno_im = 0)
		BEGIN
			INSERT @temp
			SELECT TOP 1 lno, verify_code, date
			  FROM afos_client_chop 
			 WHERE date <= @date AND lock = 1
			 ORDER BY date DESC
		END
		ELSE
		BEGIN
			INSERT @temp
			SELECT lno, verify_code, date
			  FROM (SELECT ROW_NUMBER() OVER (PARTITION BY lno ORDER BY date) AS no, lno, verify_code, date FROM afos_client_chop WHERE lno IN (@lno, @lno_im) AND date <= @date AND lock = 1) AS data
			 WHERE data.no = 1

		   DECLARE @date_lno	DATE
		   DECLARE @date_lon_im	DATE
		    SELECT @date_lno = date FROM @temp WHERE lno = @lno
			SELECT @date_lon_im = date FROM @temp WHERE lno = @lno_im

				IF (@date_lno >= @date_lon_im)
					DELETE @temp WHERE lno = @lno_im
			  ELSE
					DELETE @temp WHERE lno = @lno
		END

		INSERT @result
		SELECT lno, object
		  FROM @temp

	RETURN 
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
     EXEC sp_app_grant 'fn_GetClientChopSign', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetClientContacts.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetClientContacts') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetClientContacts;
GO

/*---------------------------------
版本 : 1.0.0
日期 : 2017-11-21
內容 : 輸入客戶編號、寄送文件類別，傳回寄送對象
type			1. Confirmation
contact_tyhpe	1.FO 2.BO 3.Accounting 4.Declaration Form 5.Master Custodian 6.Sub Custodian 7.MM 
sending_type	1.Fax 2.Email 3.Both
---------------------------------*/
CREATE FUNCTION fn_GetClientContacts (@pno INT, @type SMALLINT)
 RETURNS @contacts TABLE(contact NVARCHAR(100), contact_type SMALLINT,fax_number VARCHAR(20), email VARCHAR(100), sending_type SMALLINT, isIM BIT)
AS
BEGIN
		DECLARE @lno	INT

		 SELECT @lno = lno
		   FROM vw_contract
		  WHERE pno = @pno

		IF(@type = 1)
		BEGIN		
			DECLARE @submit_type	INT			
			DECLARE @pno_im			INT
			DECLARE @lno_im			INT

			SELECT @submit_type = cfm_submit_type,
				   @pno_im = pno_im
			  FROM vw_contract
			 WHERE pno = @pno

			SELECT @lno_im = lno
			  FROM vw_contract
			 WHERE pno = @pno_im

			 IF(@submit_type = 1)
			 BEGIN
				INSERT @contacts
				SELECT contact, contact_type, fax, '', 1, CASE lno WHEN @pno_im THEN 1 ELSE 0 END
				  FROM afos_client_contact
				 WHERE lno IN (@pno, @pno_im) AND is_for_fax = 1
			 END
			 ELSE IF (@submit_type = 2)
			 BEGIN
				INSERT @contacts
				SELECT contact, contact_type, '', email, 1, CASE lno WHEN @pno_im THEN 1 ELSE 0 END
				  FROM afos_client_contact
				 WHERE lno IN (@pno, @pno_im) AND is_for_email = 1
			 END
			 ELSE
			 BEGIN
				INSERT @contacts
				SELECT contact, contact_type, fax, '', 1, CASE lno WHEN @pno_im THEN 1 ELSE 0 END
				  FROM afos_client_contact
				 WHERE lno IN (@pno, @pno_im) AND (is_for_fax = 1 OR is_for_email = 1)
			 END		
		END
	RETURN 
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
     EXEC sp_app_grant 'fn_GetClientContacts', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetContract.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetContract') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetContract;
GO
/*------------------------------------------------------
版本 : 1.0.0
日期 : 2017/11/13
內容 : pno資料查詢，目前尚未實作資料權限之功能

INPUT
@userid 登入帳號
@date   查詢日期(預設為查詢當日)

RETURN
pno     客戶內碼
cno     客戶編號
cname   客戶名稱

-------------------------------------------------------*/

CREATE FUNCTION fn_GetContract(@userid VARCHAR(20), @date SMALLDATETIME)
  RETURNS @OrderedResult TABLE(pno INT, cp_type_wss SMALLINT, cp_type_local SMALLINT, fund_name VARCHAR(35), fund_name_im VARCHAR(35), cust_tid VARCHAR(15), cust_no VARCHAR(13), lno INT, pno_im INT)
AS
BEGIN

	--檢查是否為OnBoardingStaff
	DECLARE @isAdmin BIT
	 SELECT @isAdmin = isadmin
	   FROM app_user
	  WHERE userid = @userid
	
	IF (@userid = 'admin' OR @isAdmin = 1)
	BEGIN					
		
		INSERT @OrderedResult
		SELECT v.pno, v.cp_type_wss, v.cp_type_local, v.fund_name, v.fund_name_im, v.cust_tid, v.cust_no, v.lno, v.pno_im
		  FROM vw_contract AS v

		RETURN
	END	
	
	--此段應實作資料權限，目前尚未有相關Table
		INSERT @OrderedResult
		SELECT v.pno, v.cp_type_wss, v.cp_type_local, v.fund_name, v.fund_name_im, v.cust_tid, v.cust_no, v.lno, v.pno_im
		  FROM vw_contract AS v

	RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
	 EXEC sp_app_grant 'fn_GetContract', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetFullTraFx.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('[fn_GetFullTraFx]') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION [fn_GetFullTraFx];
GO
/*---------------------------------
版本 : 1.0.0
日期 : 2017-10-18
內容 : 取得完整外匯交易內容
---------------------------------*/

CREATE FUNCTION [fn_GetFullTraFx]()
RETURNS @result TABLE(
    [trade_no]              VARCHAR(13),
    [wss_tid]               VARCHAR(15),
    [orig_wss_tid]          VARCHAR(15),
    [trade_date]            DATE,
    [value_date]            DATE,
    [cust_tid]              VARCHAR(15),
    [pno]                   INT,
    [deal_code]             VARCHAR(2),
    [trade_type]            SMALLINT,
    [ccy_main]              CHAR(3),
    [ccy_buy]               CHAR(3),
    [amt_buy]               NUMERIC(20,5),
    [ccy_sell]              CHAR(3),
    [amt_sell]              NUMERIC(20,5),
    [base_equiv_amt]        NUMERIC(20,5),
    [rate]                  NUMERIC(20,10),
    [base_ccy]              VARCHAR(8),
    [orig_ndf_tid]          VARCHAR(15),
    [ndf_stl_ccy]           CHAR(3),
    [ndf_fix_date]          DATE,
    [swap_tid]              VARCHAR(15),
    [swap_sf]               SMALLINT,
    [swap_point]            NUMERIC(20,5),
    [orig_product_type]     SMALLINT,
    [product_type]          SMALLINT,
    [ref_no]                VARCHAR(15),
    [orig_ref_no]           VARCHAR(15),
    [status]                VARCHAR(3),
    [cancel_reason]         VARCHAR(30),
    [cancel_date]           DATE,
    [broker_type]           SMALLINT,
    [is_settled]            BIT,
    [imm_pay]               BIT,
    [imm_confirm]           BIT,
    [is_non_std_ndf]        BIT,
    [non_std_comment]       VARCHAR(100),
    [delivery_comment]      NVARCHAR(100),
    [remark1]               VARCHAR(30),
    [remark2]               VARCHAR(30),
    [remark3]               VARCHAR(30),
    [pay_nostro]            VARCHAR(10),
    [trader]                VARCHAR(3),
    [trader_name]           VARCHAR(20),
    [entry_dateime]         DATE,
    [fsi_tid]               VARCHAR(15),
    [fsi_rec_tid]           VARCHAR(15),
    [loguser]               VARCHAR(20),
    [logtime]               DATETIME,
    --tra_fx_si             
    [pay_meth]              VARCHAR(10),
    [rec_meth]              VARCHAR(10),
    [rec_nostro]            VARCHAR(10),
    [ben1]                  VARCHAR(30),
    [ben2]                  VARCHAR(30),
    [ben3]                  VARCHAR(30),
    [ben4]                  VARCHAR(30),
    [ben5]                  VARCHAR(30),
    [acc1]                  VARCHAR(30),
    [acc2]                  VARCHAR(30),
    [acc3]                  VARCHAR(30),
    [acc4]                  VARCHAR(30),
    [acc5]                  VARCHAR(30),
    [add1]                  VARCHAR(30),
    [add1b]                 VARCHAR(5),
    [add2]                  VARCHAR(30),
    [add2b]                 VARCHAR(5),
    [add3]                  VARCHAR(30),
    [add3b]                 VARCHAR(5),
    [add4]                  VARCHAR(30),
    [add4b]                 VARCHAR(5),
    [add5]                  VARCHAR(30),
    [add5b]                 VARCHAR(30),
    [add6]                  VARCHAR(30),
    [add6b]                 VARCHAR(30),
    [inter1]                VARCHAR(35),
    [inter2]                VARCHAR(35),
    [inter3]                VARCHAR(35),
    [inter4]                VARCHAR(35),
    [inter5]                VARCHAR(35),
    [city_int_no]           VARCHAR(4),
    [fsi_id]                VARCHAR(15),
    --tra_fx_cfm            
    [fx_match_pri]          BIT,
    [fx_match_sec]          BIT,
    [fx_match_swift_1]      VARCHAR(30),
    [fx_match_swift_2]      VARCHAR(30),
    [fx_match_swift_3]      VARCHAR(30),
    [fx_match_swift_4]      VARCHAR(30),
    [fx_match_swift_5]      VARCHAR(30),
    [last_action]           VARCHAR(1),
    [tag_83_swift_1]        VARCHAR(30),
    [tag_83_swift_2]        VARCHAR(30),
    [tag_83_swift_3]        VARCHAR(30),
    [tag_83_swift_4]        VARCHAR(30),
    [tag_83_swift_5]        VARCHAR(30),
    --afos_client_wss          
    [fund_code]             VARCHAR (20),
    [fund_name]             VARCHAR (35),
    --option                
    [name_trade_type]       VARCHAR(20),
    [name_swap_sf]          VARCHAR(20),
    [name_orig_product_type]VARCHAR(20),
    [name_broker_type]      VARCHAR(20),
	[name_cfm_type]         VARCHAR (200),
    --cfm_confirmed_record
	[is_cfm]                BIT,
	[cfm_time]              DATETIME,
    [cfm_type]              SMALLINT,
	[cfm_user]              VARCHAR (20)
)
AS
BEGIN
    INSERT @result
    SELECT f.*, s.pay_meth, s.rec_meth, s.rec_nostro, 
           s.ben1, s.ben2, s.ben3, s.ben4, s.ben5, 
           s.acc1, s.acc2, s.acc3, s.acc4, s.acc5, 
           s.add1, s.add1b, s.add2, s.add2b, s.add3, s.add3b, s.add4, s.add4b, s.add5, s.add5b, s.add6, s.add6b, 
           s.inter1, s.inter2, s.inter3, s.inter4, s.inter5, 
           s.city_int_no, s.fsi_id,
           ISNULL(c.fx_match_pri, 0), ISNULL(c.fx_match_sec, 0),
           c.fx_match_swift_1, c.fx_match_swift_2, c.fx_match_swift_3, c.fx_match_swift_4, c.fx_match_swift_5, 
           c.last_action, 
           c.tag_83_swift_1, c.tag_83_swift_2, c.tag_83_swift_3, c.tag_83_swift_4, c.tag_83_swift_5,
           w.fund_code, w.fund_name,
           opt2.name, opt75.name, opt73.name, opt7.name, opt516.name,
           CAST(CASE WHEN EXISTS(SELECT * FROM cfm_confirmed_record WHERE trade_no = f.trade_no) THEN 1 ELSE 0 END AS BIT),
           r.logtime, r.cfm_type, r.loguser
    FROM tra_fx f
    LEFT JOIN tra_fx_si s
    ON ((f.trade_type = 1 AND f.fsi_tid = s.wss_tid) OR (f.trade_type = 2 AND f.fsi_rec_tid = s.wss_tid))
    LEFT JOIN tra_fx_cfm c
    ON f.cust_tid = c.cust_tid
    LEFT JOIN afos_client_wss w
    ON f.pno = w.pno
    LEFT JOIN cfm_confirmed_record r
    ON f.trade_no = r.trade_no
    LEFT JOIN (SELECT item_no, name FROM app_table_field_option_item WHERE opt_no = 2) opt2
    ON f.trade_type = opt2.item_no
    LEFT JOIN (SELECT item_no, name FROM app_table_field_option_item WHERE opt_no = 75) opt75
    ON f.swap_sf = opt75.item_no
    LEFT JOIN (SELECT item_no, name FROM app_table_field_option_item WHERE opt_no = 73) opt73
    ON f.orig_product_type = opt73.item_no
    LEFT JOIN (SELECT item_no, name FROM app_table_field_option_item WHERE opt_no = 2) opt7
    ON f.broker_type = opt7.item_no
    LEFT JOIN (SELECT item_no, name FROM app_table_field_option_item WHERE opt_no = 516) opt516
    ON r.cfm_type = opt516.item_no
    RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant '[fn_GetFullTraFx]', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetPairMatchingChildren.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetPairMatchingChildren') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetPairMatchingChildren;
GO
/*------------------------------------------------------
 版本 : 1.0.1
 日期 : 2017/11/20
 內容 : 增列其他參考欄位

 版本 : 1.0.0
 日期 : 2017/11/16
 內容 : 取得指定交易配對的Children
-------------------------------------------------------*/

CREATE FUNCTION fn_GetPairMatchingChildren(@trade_no VARCHAR(13))
  RETURNS @children TABLE(trade_no VARCHAR(13), pno INT, product_type SMALLINT, trade_date DATE, value_date DATE, ccy_buy CHAR(3), amt_buy NUMERIC(20,5), ccy_sell CHAR(3), amt_sell NUMERIC(20,5), remark1 VARCHAR(30))
AS
BEGIN
	
	DECLARE @temp	TABLE(trade_no VARCHAR(13), tid VARCHAR(15))

	DECLARE @product_type	SMALLINT		-- 1. Spot 2. Forward(DF) 3.SWAP 4. NDF	
	DECLARE @swap_sf		SMALLINT
	DECLARE @ndf_settle_ccy	VARCHAR(3)
	DECLARE @ndf_fix_dt		DATE
	DECLARE @status			VARCHAR(2)
	DECLARE @remark1		VARCHAR(30)
	DECLARE @ndf_remark1	VARCHAR(30) = 'FIXING'
	
	 SELECT @product_type = product_type, 			
			@swap_sf = swap_sf,
			@ndf_settle_ccy = ndf_stl_ccy,
			@ndf_fix_dt = '',
			@status = status,
			@remark1 = remark1
	  FROM tra_fx 
	 WHERE trade_no = @trade_no

		IF @product_type IN (1,2) OR (@product_type = 3 AND @swap_sf = 1) OR (@product_type = 4 AND @remark1 = @ndf_remark1)
			RETURN

		IF @product_type = 3 -- SWAP 找 Children
	 BEGIN
			IF @status = ''
		 BEGIN
			--若為
			INSERT INTO @temp
			SELECT pair.trade_no, pair.wss_tid
			  FROM tra_fx pair
			 WHERE 1 = 1
			AND EXISTS(
				SELECT 1 FROM tra_fx fx WHERE 1=1
				   AND fx.trade_no = @trade_no
				   AND fx.value_date = pair.value_date
				   AND fx.pno = pair.pno
				   AND fx.trade_type = IIF(pair.trade_type = 1 ,2,1) -- 相反
				   AND fx.product_type = pair.product_type
				   AND (
						pair.swap_sf = 2 AND fx.rate = pair.rate
						OR
						pair.swap_sf = 1
						)
				   AND fx.ccy_buy = pair.ccy_sell
				   AND fx.ccy_sell = pair.ccy_buy
				   AND fx.trade_date < pair.trade_date
				--AND CASE WHEN fx.trade_type = 1 THEN pair.amt_sell ELSE pair.amt_buy END >= CASE WHEN fx.trade_type = 1 THEN fx.amt_buy ELSE fx.amt_sell END --待調整
				)
			AND pair.[status] = '' 
			
			INSERT INTO @temp
			SELECT pair.trade_no, pair.wss_tid
			  FROM tra_fx pair
			 WHERE 1 = 1
			AND EXISTS(
				SELECT 1 FROM  @temp AS child WHERE 1=1				
				   AND child.tid = pair.swap_tid				
				 )
			AND pair.[status] = ''

			END
		END
	   
	ELSE IF @product_type = 4 AND @remark1 != @ndf_remark1
	  BEGIN
			INSERT INTO @temp
			SELECT pair.trade_no, pair.wss_tid
			FROM tra_fx pair
			WHERE 1 = 1
			AND EXISTS(
				SELECT 1 FROM tra_fx fx WHERE 1=1				
				AND fx.value_date = pair.value_date
				AND fx.pno = pair.pno
				AND fx.trade_type = IIF(pair.trade_type = 1 ,2,1) -- 相反
				AND (
						(fx.product_type = pair.product_type AND fx.amt_buy = pair.amt_sell AND fx.amt_sell = pair.amt_buy)
						OR
						(pair.product_type = 2)
					)
				AND fx.ccy_buy = pair.ccy_sell				
				AND fx.ccy_sell = pair.ccy_buy				
				AND fx.trade_date < pair.trade_date
				--AND fx.ndf_fix_date = pair.trade_date
				 )
			AND pair.[status] = 'F'
			AND pair.remark1 = @ndf_remark1
	    END

		INSERT @children
		SELECT t.trade_no, f.pno, f.product_type, f.trade_date, f.value_date, f.ccy_buy, f.amt_buy, f.ccy_sell, f.amt_sell, f.remark1
		  FROM @temp AS t, tra_fx AS f

	RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
	 EXEC sp_app_grant 'fn_GetPairMatchingParents', 'ALL';
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetPairMatchingParents.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetPairMatchingParents') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetPairMatchingParents;
GO
/*------------------------------------------------------
 版本 : 1.0.0
 日期 : 2017/11/20
 內容 : 增列其他參考欄位

 版本 : 1.0.0
 日期 : 2017/11/16
 內容 : 取得指定交易配對的Parents
-------------------------------------------------------*/

CREATE FUNCTION fn_GetPairMatchingParents(@trade_no VARCHAR(13))
  RETURNS @parents TABLE(trade_no VARCHAR(13),pno INT, product_type SMALLINT, trade_date DATE, value_date DATE, ccy_buy CHAR(3), amt_buy NUMERIC(20,5), ccy_sell CHAR(3), amt_sell NUMERIC(20,5), reamrk1 VARCHAR(30))
AS
BEGIN
	
	DECLARE @product_type	SMALLINT		-- 1. Spot 2. Forward(DF) 3.SWAP 4. NDF
	DECLARE @swap_tid		VARCHAR (15)
	DECLARE @swap_sf		SMALLINT
	DECLARE @ndf_settle_ccy	VARCHAR(3)
	DECLARE @ndf_fix_dt		DATE
	DECLARE @status			VARCHAR(2)	

	 SELECT @product_type = product_type, 
			@swap_tid = swap_tid, 
			@swap_sf = swap_sf,
			@ndf_settle_ccy = ndf_stl_ccy,
			@ndf_fix_dt = '',
			@status = status
	  FROM tra_fx 
	 WHERE trade_no = @trade_no

		IF @product_type = 3 -- Forward、SWAP 找 Parent
	 BEGIN
			IF @status = ''
		 BEGIN
			--若為 F 則為 Unwind 反之若為 S 則為 Rollover
			INSERT INTO @parents
			SELECT pair.trade_no, pair.pno, pair.product_type, pair.trade_date, pair.value_date, pair.ccy_buy, pair.amt_buy, pair.ccy_sell, pair.amt_sell, remark1
			  FROM tra_fx pair
			 WHERE 1 = 1
			AND EXISTS(
				SELECT 1 FROM tra_fx fx WHERE 1=1
				   AND fx.trade_no = @trade_no
				AND fx.value_date = pair.value_date
				AND fx.pno = pair.pno
				AND fx.trade_type = IIF(pair.trade_type = 1 ,2,1) -- 相反
				AND fx.product_type = pair.product_type
				AND fx.rate = pair.rate
				AND fx.ccy_buy = pair.ccy_sell
				AND fx.ccy_sell = pair.ccy_buy
				AND fx.trade_date > pair.trade_date
				--AND CASE WHEN fx.trade_type = 1 THEN pair.amt_sell ELSE pair.amt_buy END >= CASE WHEN fx.trade_type = 1 THEN fx.amt_buy ELSE fx.amt_sell END --待調整
				)
			AND pair.[status] = '' 
			AND pair.swap_sf = 2

			--若為 S 則為 Unwind 反之若為 F 則為 Rollover
			INSERT INTO @parents
			SELECT pair.trade_no, pair.pno, pair.product_type, pair.trade_date, pair.value_date, pair.ccy_buy, pair.amt_buy, pair.ccy_sell, pair.amt_sell, remark1
			  FROM tra_fx pair
			 WHERE 1 = 1
			AND EXISTS(
				SELECT 1 FROM tra_fx fx WHERE 1=1
				AND fx.wss_tid = @swap_tid
				AND fx.value_date = pair.value_date
				AND fx.pno = pair.pno
				AND fx.trade_type = IIF(pair.trade_type = 1 ,2,1) -- 相反
				AND fx.product_type = pair.product_type			
				AND fx.ccy_buy = pair.ccy_sell
				AND fx.ccy_sell = pair.ccy_buy
				AND fx.trade_date > pair.trade_date
				--AND CASE WHEN fx.trade_type = 1 THEN pair.amt_sell ELSE pair.amt_buy END >= CASE WHEN fx.trade_type = 1 THEN fx.amt_buy ELSE fx.amt_sell END --待調整
				 )
			AND pair.[status] = ''
			AND pair.swap_sf = 2
			END
		END
	   ELSE IF @status = 'S' AND @product_type = 2
	  BEGIN
			INSERT INTO @parents
			SELECT pair.trade_no, pair.pno, pair.product_type, pair.trade_date, pair.value_date, pair.ccy_buy, pair.amt_buy, pair.ccy_sell, pair.amt_sell, remark1
			FROM tra_fx pair
			WHERE 1 = 1
			AND EXISTS(
				SELECT 1 FROM tra_fx fx WHERE 1=1				
				AND fx.value_date = pair.value_date
				AND fx.pno = pair.pno
				AND fx.trade_type = IIF(pair.trade_type = 1 ,2,1) -- 相反				
				AND fx.ccy_buy = pair.ccy_sell
				AND fx.ccy_sell = pair.ccy_buy
				AND fx.trade_date > pair.trade_date
				--AND fx.trade_date = pair.ndf_fix_date
				 )
			--AND pair.[status] = 'F'
			AND pair.product_type = 4
		END
	ELSE IF @status = 'F' AND @product_type = 4
	  BEGIN
			INSERT INTO @parents
			SELECT pair.trade_no, pair.pno, pair.product_type, pair.trade_date, pair.value_date, pair.ccy_buy, pair.amt_buy, pair.ccy_sell, pair.amt_sell, remark1
			FROM tra_fx pair
			WHERE 1 = 1
			AND EXISTS(
				SELECT 1 FROM tra_fx fx WHERE 1=1				
				AND fx.value_date = pair.value_date
				AND fx.pno = pair.pno
				AND fx.trade_type = IIF(pair.trade_type = 1 ,2,1) -- 相反
				AND fx.product_type = pair.product_type			
				AND fx.ccy_buy = pair.ccy_sell
				AND fx.amt_buy = pair.amt_sell
				AND fx.ccy_sell = pair.ccy_buy
				AND fx.amt_sell = pair.amt_buy
				AND fx.trade_date > pair.trade_date
				--AND fx.trade_date = pair.ndf_fix_date
				 )
			AND pair.[status] = 'F'
			AND pair.product_type = 4
	    END
	RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
	 EXEC sp_app_grant 'fn_GetPairMatchingParents', 'ALL';
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetWaitingToLockAfosList.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('[fn_GetWaitingToLockAfosList]') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION [fn_GetWaitingToLockAfosList];
GO
/*---------------------------------
版本 : 1.0.1
日期 : 2017-10-16
內容 : 欄位異動

版本 : 1.0.0
日期 : 2017-09-27
內容 : 顯示 AFOS 客戶主檔覆核清單
---------------------------------*/

CREATE FUNCTION [fn_GetWaitingToLockAfosList]()
RETURNS @result TABLE(
    lno INT, cust_no VARCHAR(13), fund_code VARCHAR(20), status INT, mod_status INT)
BEGIN
    
    --Pending
    INSERT @result
    SELECT l.lno, l.cust_no, w.fund_code, l.status, l.mod_status
    FROM afos_client_local l
    LEFT JOIN (SELECT cust_no, fund_code FROM afos_client_wss WHERE cust_no <> '') w
    ON l.cust_no = w.cust_no
    WHERE l.status = 1 AND l.mod_status = 2 
    --2.Waiting For Approval(Active)
    
    --Active
    INSERT @result
    SELECT l.lno, l.cust_no, w.fund_code, l.status, l.mod_status
    FROM afos_client_local l
    LEFT JOIN (SELECT cust_no, fund_code FROM afos_client_wss WHERE cust_no <> '') w
    ON l.cust_no = w.cust_no
    WHERE l.status = 2 AND l.mod_status BETWEEN 3 AND 5    
    --3.Waiting For Approval(Modifying)
    --4.Waiting For Approval(Close)
    --5.Waiting For Approval(Delete)    
            
    RETURN 
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant '[fn_GetWaitingToLockAfosList]', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_getworkdayHHmmss.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_getworkdayHHmmss') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_getworkdayHHmmss;
GO
/*------------------------------------------------------
 版本 : 1.0.0
 日期 : 2014/09/03
 內容 : 取得營業日 (最新日初日)
-------------------------------------------------------*/

CREATE FUNCTION fn_getworkdayHHmmss()
  RETURNS DATETIME
AS
BEGIN
	DECLARE @workday DATETIME = '1900-01-01'
	SELECT @workday = excdate FROM dbo.pro_date WHERE pno = 0 AND proctp = 1	
	DECLARE @hour INT, @minute INT, @second INT
	SELECT @workday = DATEADD(HOUR, DATEPART(HOUR, GETDATE()), @workday)
	SELECT @workday = DATEADD(MINUTE, DATEPART(MINUTE, GETDATE()), @workday)
	SELECT @workday = DATEADD(SECOND, DATEPART(SECOND, GETDATE()), @workday)
	RETURN @workday
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
	 EXEC sp_app_grant 'fn_getworkdayHHmmss', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_GetWorkingDay.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetWorkingDay') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetWorkingDay;
GO

/*---------------------------------
版本 : 1.0.0
日期 : 2016-08-19
內容 : 判斷T + N當中的T是否為交易日，如果為非交易日的話先將T改寫為下一個工作日後再處理T + N
  EX : 2016-07-31星期日為假日，
     offset = -1 => 07-29(五)
     offset =  0 => 08-01(一)
     offset =  1 => 08-02(二)
     offset =  2 => 08-03(三)
 
     2016-08-01(一) 為上班日
     offset = -1 => 07-29(五)
     offset =  0 => 08-01(一)
     offset =  1 => 08-02(二)
     offset =  2 => 08-03(三)
---------------------------------*/
CREATE FUNCTION fn_GetWorkingDay
	(@input_date DATE, @calendar_target VARCHAR(10), @calendar_catalog INT,@offset INT)
 RETURNS DATE 
AS
BEGIN

	--估計一年的工作天為200天，再加減需要幾年
	DECLARE @offset_year INT = ABS(@offset)/ 200 +1
	DECLARE @date DATE
	DECLARE @zero_date DATE ,@correct_zero_base INT = 1

	SELECT TOP(1) @zero_date =  date_to_work 
		FROM (SELECT * FROM fn_GetCalendar(@input_date,@calendar_target,@calendar_catalog,@offset_year)) as ca
		WHERE date_to_work >=@input_date AND is_working_date = 1 ORDER BY date_to_work ASC
--RETURN  DATEADD(dd,@offset_year,@input_date)

	IF (@offset >= 0)
		BEGIN
			;WITH CTE AS
			(
			SELECT date_to_work, is_working_date FROM fn_GetCalendar(@input_date,@calendar_target,@calendar_catalog,@offset_year)
			WHERE is_working_date = 1
			AND date_to_work >=  @zero_date
			)
			SELECT TOP(@offset + @correct_zero_base) @date =  date_to_work FROM CTE
			ORDER BY date_to_work ASC
		END
	ELSE
		BEGIN
			;WITH CTE AS
			(
			SELECT date_to_work, is_working_date FROM fn_GetCalendar(@input_date,@calendar_target,@calendar_catalog,@offset_year)
			WHERE is_working_date = 1
			AND @zero_date >= date_to_work
			)
			SELECT TOP(ABS(@offset) + @correct_zero_base) @date =  date_to_work FROM CTE	
			ORDER BY date_to_work DESC
		END
	RETURN ISNULL(@date,'19000101')
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
     EXEC sp_app_grant 'fn_GetWorkingDay', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\fn_proctp.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_proctp') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_proctp;
GO
/*------------------------------------------------------
 版本 : 1.0.0
 日期 : 2014/09/03
 內容 : 得到契約的結帳狀態
-------------------------------------------------------*/

CREATE FUNCTION fn_proctp(@pno int)
  RETURNS @list TABLE(pno INT, proctp INT, native INT,excdate SMALLDATETIME,nexttp INT,nextdate SMALLDATETIME)
AS
BEGIN
	DECLARE @mdt SMALLDATETIME
	DECLARE @proctp INT,@native INT,@end INT,@nexttp INT,@nextdate SMALLDATETIME,@country VARCHAR(5)
	
		
	SELECT @mdt=MAX(excdate) from pro_date where pno=@pno

	SELECT TOP 1  @proctp=proctp,@native=native,@end=isend 
	FROM pro_date WHERE pno=@pno AND excdate=@mdt
 	ORDER BY excdate,proctp DESC 
 
	IF (@end=0)
	BEGIN
			SELECT @nexttp=MIN(proctp) FROM pro_date WHERE pno=@pno AND proctp>@proctp 
			SELECT @nextdate=@mdt
	END ELSE
	BEGIN
			SELECT @nexttp=MIN(proctp) FROM pro_date WHERE pno=@pno	
			SELECT @nextdate=dbo.fn_GetWorkingDay(@mdt,'TWD',1,1) --抓'TWD'
			--SELECT @nextdate=DATEADD(DAY,1,@mdt) --先抓日曆日
	END	
 
 	INSERT @list
 	VALUES(@pno,ISNULL(@proctp,0),ISNULL(@native,0),ISNULL(@mdt,0),ISNULL(@nexttp,0),ISNULL(@nextdate,0))
    
 	RETURN;

END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
	 EXEC sp_app_grant 'fn_proctp', 'ALL';
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\ETL\fn_GetPKSeqNo.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('[fn_GetPKSeqNo]') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION [fn_GetPKSeqNo];
GO
/*---------------------------------
版本 : 1.0.0
日期 : 
內容 : 

INPUT

RETURN
---------------------------------*/

CREATE FUNCTION [fn_GetPKSeqNo](@leading_code CHAR(3))
RETURNS CHAR(10)
BEGIN
    DECLARE @max_code CHAR(10)
    
    IF @leading_code = 'equ'    
      SELECT @max_code = ISNULL(MAX(code), '') FROM cmn_equity
    ELSE IF @leading_code = 'bnd'
      SELECT @max_code = ISNULL(MAX(code), '') FROM cmn_bond
    ELSE IF @leading_code = 'fnd'
      SELECT @max_code = ISNULL(MAX(code), '') FROM cmn_fund    
    ELSE IF @leading_code = 'eln'    
      SELECT @max_code = ISNULL(MAX(code), '') FROM cmn_eln    
    ELSE IF @leading_code = 'pgn'
      SELECT @max_code = ISNULL(MAX(code), '') FROM cmn_pgn
    ELSE 
      RETURN ''
    
    DECLARE @seq VARCHAR(7)
    IF @max_code = ''
      SET @seq = '0000001'          
    ELSE
    BEGIN      
      SET @seq = CAST(CAST(SUBSTRING(@max_code, 4, 7) AS INT) + 1 AS VARCHAR(7))
      SET @seq = REPLICATE(0, 7 - LEN(@seq)) + @seq    
    END
    RETURN @leading_code + @seq
    
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant '[fn_GetPKSeqNo]', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\ETL\fn_joblist.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_joblist') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_joblist;
GO
/*---------------------------------
版本 : 1.0.4
日期 : 2015/07/21 
內容 : 新增排序

版本 : 1.0.3
日期 : 2014/06/20 
內容 : 新增收信並解壓縮附檔

版本 : 1.0.2
日期 : 2014/04/10 
內容 : 新增匯出檔案

版本 : 1.0.1
日期 : 2012-10-11 匯入檔名改抓 app_etl_set
內容 : get job list (0=all)
---------------------------------*/

CREATE FUNCTION fn_joblist(@jobindex INT)
  RETURNS @list TABLE 
  (
    jobindex INT, jobname VARCHAR(50), id VARCHAR(20), name VARCHAR(60),
    transform_type SMALLINT, impfilename VARCHAR(1000), usecolumnname BIT,
    source_from VARCHAR(20), source_into VARCHAR(20), rundatetp SMALLINT, rundate SMALLDATETIME, jobtype SMALLINT,
    mail_ok VARCHAR(200),mail_error VARCHAR(200), jobcalendar VARCHAR(10), seq INT, fetch_id VARCHAR(20))
AS
BEGIN
    --匯入資料庫
	INSERT @list
	SELECT a.jobindex, a.jobname, b.id, c.name, c.transform_type, c.source_filename, c.usecolumnname,
	       c.source_from, c.source_into, b.rundatetp, GETDATE(), b.type, 
	       b.mail_ok, b.mail_error, a.jobcalendar, b.seq, ''
	FROM app_etl_jobdef a,app_etl_joblist b,app_etl_set c
	WHERE a.jobindex=b.jobindex AND b.id=c.id AND (a.jobindex=@jobindex OR @jobindex=0) 
    ORDER BY b.seq ASC
    
    --更新來源資料檔
    UPDATE @list 
       SET fetch_id = i.id
         , impfilename = CASE i.is_unzip WHEN 1 THEN i.unzip_file_path ELSE i.file_path END
		 , transform_type = i.transform_type
      FROM @list l, app_etl_import_data i
     WHERE l.impfilename = i.id
     
    --匯出資料
    INSERT @list
	SELECT a.jobindex, a.jobname, b.id, c.name, c.file_type, c.file_name, c.has_caption,
	       '', '', b.rundatetp, GETDATE(), b.type, 
	       b.mail_ok, b.mail_error, a.jobcalendar, b.seq, ''
	FROM app_etl_jobdef a,app_etl_joblist b, app_etl_export c
	WHERE a.jobindex=b.jobindex AND b.id=c.id AND (a.jobindex=@jobindex OR @jobindex=0) 
    ORDER BY b.seq ASC
	
	--預儲程序, 外部執行檔, SQL 語法
	INSERT @list
	SELECT a.jobindex, a.jobname, b.id, c.runname, c.runtp + 3, '' , 0,
	       '', '', b.rundatetp, GETDATE(), b.type,
	       b.mail_ok, b.mail_error, a.jobcalendar, b.seq, ''
	FROM app_etl_jobdef a,app_etl_joblist b, app_runer_def c
	WHERE a.jobindex=b.jobindex AND b.id=c.runid AND (a.jobindex=@jobindex OR @jobindex=0) 
    ORDER BY b.seq ASC
    
    --外送檔案
    INSERT @list
	SELECT a.jobindex, a.jobname, b.id, c.name, '', c.file_name, 0,
	       '', '', b.rundatetp, GETDATE(), b.type, 
	       b.mail_ok, b.mail_error, a.jobcalendar, b.seq, ''
	FROM app_etl_jobdef a,app_etl_joblist b, app_etl_deliver_setting c
	WHERE a.jobindex=b.jobindex AND b.id=c.id AND (a.jobindex=@jobindex OR @jobindex=0) 
    ORDER BY b.seq ASC
 
	RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_joblist', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\ETL\fn_schedulerlist.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_schedulerlist') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_schedulerlist;
GO
/*---------------------------------
版本 : 1.0.1
日期 : 2014-06-20
內容 : 
因應執行順序，加入 [seq] 欄位
因應營業日，加入 [jobcalendar] 欄位
       
版本 : 1.0.0
日期 : 2012-09-11
內容 : get scheduler list 
---------------------------------*/

CREATE FUNCTION fn_schedulerlist(@sid VARCHAR(20))
  RETURNS @list TABLE (jobindex INT,jobname VARCHAR(50),id VARCHAR(20),name VARCHAR(60),
  transform_type SMALLINT,impfilename VARCHAR(1000),usecolumnname BIT,
  source_from VARCHAR(20),source_into VARCHAR(20),rundatetp SMALLINT,rundate SMALLDATETIME,jobtype SMALLINT,
  mail_ok VARCHAR(200),mail_error VARCHAR(200), jobcalendar VARCHAR(10), seq INT, fetch_id VARCHAR(20))
AS
BEGIN
    --匯入
	INSERT @list
 	SELECT a.jobindex,a.jobname,b.id,c.name,c.transform_type,c.source_filename ,c.usecolumnname,
	c.source_from,c.source_into,b.rundatetp,GETDATE(),b.type,b.mail_ok,b.mail_error, a.jobcalendar, b.seq, ''
	FROM app_etl_jobdef a,app_etl_joblist b,app_etl_set c,app_scheduler_set d
	WHERE a.jobindex=b.jobindex AND b.id=c.id AND b.jobindex = d.jobindex
	AND d.sid=@sid AND b.type = 1
	
	--更新來源資料檔
    UPDATE @list 
       SET fetch_id = i.id
         , impfilename = CASE i.is_unzip WHEN 1 THEN i.unzip_file_path ELSE i.file_path END
		 , transform_type = i.transform_type
      FROM @list l, app_etl_import_data i
     WHERE l.impfilename = i.id
	
	--匯出
	INSERT @list
 	SELECT a.jobindex,a.jobname,b.id,c.name,c.file_type,c.file_name ,c.has_caption,
	'','',b.rundatetp,GETDATE(),b.type,b.mail_ok,b.mail_error, a.jobcalendar, b.seq, ''
	FROM app_etl_jobdef a,app_etl_joblist b,app_etl_export c,app_scheduler_set d
	WHERE a.jobindex=b.jobindex AND b.id=c.id AND b.jobindex = d.jobindex
	AND d.sid= @sid AND b.type = 2
 
    --預儲程序, 外部執行檔, SQL 語法
    INSERT @list
 	SELECT a.jobindex,a.jobname,b.id,c.runname, c.runtp + 3, '' , 0,
	'','',b.rundatetp,GETDATE(),b.type,b.mail_ok,b.mail_error, a.jobcalendar, b.seq, ''
	FROM app_etl_jobdef a,app_etl_joblist b,app_runer_def c,app_scheduler_set d
	WHERE a.jobindex=b.jobindex AND b.id=c.runid AND b.jobindex = d.jobindex
	AND d.sid=@sid AND b.type BETWEEN 4 AND 6
	
	--外送檔案
    INSERT @list
	SELECT a.jobindex, a.jobname, b.id, c.name, '', c.file_name, 0,
	       '', '', b.rundatetp, GETDATE(), b.type, 
	       b.mail_ok, b.mail_error, a.jobcalendar, b.seq, ''
	FROM app_etl_jobdef a,app_etl_joblist b,app_etl_deliver_setting c,app_scheduler_set d
	WHERE a.jobindex=b.jobindex AND b.id=c.id AND b.jobindex = d.jobindex
	AND d.sid= @sid AND b.type = 7

  RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_schedulerlist', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\??????fn_CbReport03.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('[fn_CbReport03]') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION [fn_CbReport03];
GO

/*---------------------------------
版本：1.0.0
日期：2015/06/18
內容：央行媒體申報 3:外匯(收入/支出)交易日報資料傳輸檔案格式
---------------------------------*/
CREATE FUNCTION fn_CbReport03(
	@date SMALLDATETIME)
RETURNS @tmp TABLE(
	type			SMALLINT,
	[DATA-DATE]   	SMALLDATETIME,
	[BANK]        	CHAR(2),
	[E-I-CODE]    	CHAR(1),
	[CURR]        	CHAR(3),
	[ITEM]        	CHAR(2),
	[EXCHG-NORM]  	NUMERIC(15,3),
	[EXCHG-CORR]  	NUMERIC(15,3),
	[STORE-FORE-N]	NUMERIC(15,3),
	[STORE-FORE-C]	NUMERIC(15,3),
	[NO-EXCHG-O-N]	NUMERIC(15,3),
	[NO-EXCHG-O-C]	NUMERIC(15,3),
	[LINE-TOT-N]  	NUMERIC(15,3),
	[LINE-TOT-C]  	NUMERIC(15,3))
BEGIN
	--DECLARE @bank_osu VARCHAR(2) = (SELECT SUBSTRING(opt_value,1,2) 
	--							FROM app_option 
	--							WHERE opt_name = 'CB_BANK_OSU')

	DECLARE @bank_fagn VARCHAR(2) = 'GN'

	DECLARE @t_income TABLE(
	type			SMALLINT,
	ccy				CHAR(3),
	[ITEM]			CHAR(2),
	en				NUMERIC(15,3),
	ec				NUMERIC(15,3),
	sfn				NUMERIC(15,3),
	sfc				NUMERIC(15,3),
	neon			NUMERIC(15,3),
	neoc			NUMERIC(15,3)
	)
	INSERT @t_income
	SELECT  1,ccy,
			CASE WHEN kind_code = '1' THEN '10'
				 WHEN kind_code = '2' THEN '20'
				 WHEN kind_code = '3' THEN '30'
				 WHEN kind_code = '4' THEN '40'
				 WHEN kind_code = '5' THEN '50'
				 WHEN kind_code = '6' THEN '60'
				 END [ITEM],
				CASE data_kind WHEN '0' THEN amt_in ELSE 0 END en,
				0,
				CASE WHEN data_kind IN ('1','2','3','6') THEN amt_in ELSE 0 END sfn,
            	0,
            	CASE WHEN data_kind IN ('4','5','7') THEN amt_in ELSE 0 END neon,
            	0
            FROM cb_cashflow
            WHERE date = @date AND amt_in > 0 AND ccy <> 'TWD'
            
    DECLARE @t_expense TABLE(
    type			SMALLINT,
	ccy				CHAR(3),
	[ITEM]			CHAR(2),
	en				NUMERIC(15,3),
	ec				NUMERIC(15,3),
	sfn				NUMERIC(15,3),
	sfc				NUMERIC(15,3),
	neon			NUMERIC(15,3),
	neoc			NUMERIC(15,3)
	)
	INSERT @t_expense
	SELECT 1,ccy,
			CASE WHEN kind_code = '1' THEN '10'
				 WHEN kind_code = '2' THEN '20'
				 WHEN kind_code = '3' THEN '30'
				 WHEN kind_code = '4' THEN '40'
				 WHEN kind_code = '5' THEN '50'
				 WHEN kind_code = '6' THEN '60'
				 END [ITEM],
				CASE data_kind WHEN '0' THEN amt_out ELSE 0 END en,
				0,
				CASE WHEN data_kind IN ('1','2','3','6') THEN amt_out ELSE 0 END sfn,
            	0,
            	CASE WHEN data_kind IN ('4','5','7') THEN amt_out ELSE 0 END neon,
            	0
            FROM cb_cashflow
            WHERE date = @date AND amt_out > 0 AND ccy <> 'TWD'

    INSERT @tmp
    SELECT type,@date,'','E',ccy,ITEM,ROUND(SUM(en),2),ROUND(SUM(ec),2),ROUND(SUM(sfn),2),ROUND(SUM(sfc),2),
    ROUND(SUM(neon),2),ROUND(SUM(neoc),2),0,0 
    FROM @t_income
    GROUP BY ccy,ITEM,type
    
    INSERT @tmp
    SELECT type,@date,'','E',ccy,99,ROUND(SUM(en),2),ROUND(SUM(ec),2),ROUND(SUM(sfn),2),ROUND(SUM(sfc),2),
    ROUND(SUM(neon),2),ROUND(SUM(neoc),2),0,0 
    FROM @t_income
    GROUP BY ccy,type
    
    /**/
    INSERT @tmp
    SELECT type,@date,'','I',ccy,ITEM,ROUND(SUM(en),2),ROUND(SUM(ec),2),ROUND(SUM(sfn),2),ROUND(SUM(sfc),2),
    ROUND(SUM(neon),2),ROUND(SUM(neoc),2),0,0 
    FROM @t_expense
    GROUP BY ccy,ITEM,type
    
    INSERT @tmp
    SELECT type,@date,'','I',ccy,99,ROUND(SUM(en),2),ROUND(SUM(ec),2),ROUND(SUM(sfn),2),ROUND(SUM(sfc),2),
    ROUND(SUM(neon),2),ROUND(SUM(neoc),2),0,0 
    FROM @t_expense
    GROUP BY ccy,type
    
    UPDATE @tmp
	SET BANK = @bank_fagn
	WHERE type =1
    
    UPDATE @tmp SET [LINE-TOT-N] = [EXCHG-NORM]+[STORE-FORE-N]+[NO-EXCHG-O-N],
					[LINE-TOT-C] = [EXCHG-CORR]+[STORE-FORE-C]+[NO-EXCHG-O-C]
	UPDATE @tmp SET [LINE-TOT-C]=[LINE-TOT-C]/100,[LINE-TOT-N]=[LINE-TOT-N]/100,
					[EXCHG-NORM]=[EXCHG-NORM]/100,[EXCHG-CORR]=[EXCHG-CORR]/100,
					[STORE-FORE-N]=[STORE-FORE-N]/100,[STORE-FORE-C]=[STORE-FORE-C]/100,
					[NO-EXCHG-O-N]=[NO-EXCHG-O-N]/100,[NO-EXCHG-O-C]=[NO-EXCHG-O-C]/100
					WHERE CURR IN ('JPY','TRL')
	RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant '[fn_CbReport03]', 'ALL';
GO	




GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\??????fn_DENUMERIC.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('[fn_DENUMERIC]') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION [fn_DENUMERIC];
GO

/*---------------------------------
版本：1.0.0
日期：2015/07/16
內容：將媒體三、四使用的數字格式轉回NUMERIC
---------------------------------*/
CREATE FUNCTION fn_DENUMERIC(@NumStr CHAR(14))
RETURNS NUMERIC(15,3)
BEGIN	
	DECLARE @dec_part INT = CAST(SUBSTRING(@NumStr,13,2) AS INT)	
	DECLARE @int_part BIGINT = CAST(SUBSTRING(@NumStr,2,11) AS BIGINT)	
	DECLARE @sign INT = CASE SUBSTRING(@NumStr,1,1) WHEN ' ' THEN 1 ELSE -1 END
	
	DECLARE @result NUMERIC(15,3)=@sign*(@int_part+@dec_part/100.00)
		
	RETURN @result
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_DENUMERIC', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\??????fn_NUMERIC.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('[fn_NUMERIC]') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION [fn_NUMERIC];
GO

/*---------------------------------
版本：1.0.0
日期：2015/07/16
內容：媒體三、四使用的數字格式，PIC:S9(11)V99，長度14
---------------------------------*/
CREATE FUNCTION fn_NUMERIC(@Num NUMERIC(13,2))
RETURNS CHAR(14)
BEGIN		
	DECLARE @sign CHAR(1) = CASE WHEN @Num >= 0 THEN ' ' ELSE '-' END
	DECLARE @str VARCHAR(13) =  REPLACE(CAST(ABS(@Num) AS VARCHAR(14)),'.','')
	DECLARE @result CHAR(14) = @sign + REPLACE(STR(@str,13),' ','0')			
	RETURN @result
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_NUMERIC', 'ALL';
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\??????fn_UpdateCashFlowCb.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('[fn_UpdateCashFlowCb]') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION [fn_UpdateCashFlowCb];
GO
/*---------------------------------
版本 : 1.0.0
日期 : 2017/11/20
內容 : 設定資金異動檔央行申報選項設定

INPUT 
@cash_flow   現金資金異動暫存檔
@pno         契約序號
@date        執行日期

RETURN 央行申報資金暫存檔
---------------------------------*/

CREATE FUNCTION [fn_UpdateCashFlowCb](@cash_flow tp_cash_flow READONLY, @pno INT, @date DATE)
RETURNS @result TABLE
(   
    pno               INT            
  , [date]            DATE  
  , seq               INT                
  , trade_no          VARCHAR(40)
  , value_date		  DATE					           --��Τ��
  , cp_type           SMALLINT
  ,	product_type      SMALLINT 			               --�ӫ~���O
  ,	swap_sf           SMALLINT
  ,	type              SMALLINT
  ,	trade_status      SMALLINT
  ,	orig_trade_no     VARCHAR(13)
  , orig_trade_amt    NUMERIC(20,5)
  , trade_type		  SMALLINT
  , cb_trade_type	  CHAR(2)
  , ccy               CHAR(3)         
  , amt_in            NUMERIC(20,5)  
  , amt_out           NUMERIC(20,5)  
  , exch_rate         NUMERIC(11,8) 
  , bal_amt           NUMERIC(20,5)   
  , note              VARCHAR(100)   
  , data_no           VARCHAR(12)
  , country_source    VARCHAR(5)     
  , [class]           VARCHAR(3)     
  , class_detail      VARCHAR(3)     
  , kind_code         VARCHAR(3)     
  , forward_spl       VARCHAR(3)     
  , data_source       VARCHAR(3)     
  , data_kind         VARCHAR(3)     
  , oppo_name         VARCHAR(40)    
  , rem_type          VARCHAR(3)     
  , swift_bank        VARCHAR(16)    
  , data_source2      VARCHAR(1)     
  , bank              VARCHAR(12)    
  , bankacc           VARCHAR(14)    
  , cp_bank           VARCHAR(12)    
  , cp_bankacc        VARCHAR(14)
  , approv_no_flag    VARCHAR(1)
  , forward_settle    VARCHAR(3)
)
BEGIN
    DECLARE @tmp tp_cash_flow
    INSERT @tmp
    SELECT * FROM @cash_flow
    
    DECLARE @row_count INT
    SELECT @row_count = COUNT(*) FROM @cash_flow

--�򥻸�T��
    DECLARE @afos_client_local TABLE
    (
        pno			INT
	  , acc_name	VARCHAR(150) --Account Name
	  , cp_type		SMALLINT     --Counterparty Type 
    )
    INSERT @afos_client_local
    SELECT b.pno
		 , acc_name
		 , cp_type
		 FROM afos_client_local a
		 LEFT JOIN vw_contract b ON a.lno = b.lno
		 WHERE b.pno = @pno
    
--��s�a�ϰ�O
    UPDATE @tmp 
       SET country_source
	     = CASE
		 WHEN t.acc1 = 'XINTERNAL' THEN 'TW'
		 ELSE SUBSTRING(t.acc1,4,2)
		 END
      FROM @tmp r, tra_fx_si t

--��s�������
	UPDATE @tmp
		SET [class] 
			= ''

--��s����Ӥ���
	UPDATE @tmp
		SET[class_detail]
		= ''

--��s�������
	 UPDATE @tmp
		SET cb_trade_type
		 = ''

--��s note
    UPDATE @tmp
       SET note = ''

--��s��ڸ��X�e��r
    UPDATE @tmp 
       SET data_no = ''

--��s���������O
    UPDATE @tmp
       SET kind_code 
         = '3'

--��s��ڸ��X
    DECLARE @year VARCHAR(2) = SUBSTRING(CONVERT(VARCHAR(6), @date, 12), 1, 2)

	DECLARE @leading VARCHAR(10)
	SELECT @leading = SUBSTRING(ISNULL(opt_value, 'FAGN'), 3, 2) FROM app_option WHERE opt_name = 'CB_BANK_FAGN'
	
    DECLARE @prefix_in CHAR(6) = @leading + @year + '3O'

    DECLARE @data_no_in INT
    SELECT @data_no_in 
         = CAST(ISNULL(MAX(SUBSTRING(data_no, 7, 6)), 0) AS INT) 
      FROM cb_cashflow 
     WHERE data_no 
      LIKE @prefix_in + '[0-9]%'
    
    DECLARE @tmp_in TABLE
    (
        seq INT
      , data_no VARCHAR(12)
    )
    INSERT @tmp_in
    SELECT seq
         , @prefix_in 
         + REPLACE
         (  
            STR
            (  
               CAST
               (  
                  @data_no_in + ROW_NUMBER() OVER(ORDER BY seq ASC) AS VARCHAR(6) 
               )
               , 6
            )
            , SPACE(1), '0'
         )
       FROM @tmp
      WHERE trade_type = 1
      
     UPDATE @tmp
        SET data_no = i.data_no
       FROM @tmp t, @tmp_in i
      WHERE t.trade_type = 1 
        AND t.seq = i.seq

    DECLARE @prefix_out CHAR(6) = @leading + @year + '5O'

    DECLARE @data_no_out INT
    SELECT @data_no_out 
         = CAST(ISNULL(MAX(SUBSTRING(data_no, 7, 6)), 0) AS INT) 
      FROM cb_cashflow 
     WHERE data_no 
      LIKE @prefix_out + '[0-9]%'
      
   DECLARE @tmp_out TABLE
    (
        seq INT
      , data_no VARCHAR(12)
    )
    INSERT @tmp_out
    SELECT seq
         , @prefix_out
         + REPLACE
         (  
            STR
            (  
               CAST
               (  
                  @data_no_out + ROW_NUMBER() OVER(ORDER BY seq ASC) AS VARCHAR(6) 
               )
               , 6
            )
            , SPACE(1), '0'
         )
       FROM @tmp
      WHERE trade_type = 2 
      
     UPDATE @tmp
        SET data_no = i.data_no
       FROM @tmp t, @tmp_out i
      WHERE t.trade_type = 2 
        AND t.seq = i.seq
        
--��s�~�׷~�ȶ���
    UPDATE @tmp 
       SET forward_spl 
         = ''

--��s�~�רӷ��Υh�B
    UPDATE @tmp
       SET data_source 
         = ''

--�Ѵڤ�ú�ڤ覡(��ڧO)
    UPDATE @tmp
       SET data_kind = '0'

--��s��/���ڤH�����O
    UPDATE @tmp 
       SET rem_type 
         = '3'

--��~�״ڻȦ�SWIFT-CODE
    UPDATE @tmp
       SET swift_bank 
         = ''

    UPDATE @tmp
       SET swift_bank 
         = SUBSTRING(t.acc1,0,4)
	 FROM @tmp r, tra_fx_si t, cmn_broker b, afos_client_wss w
     WHERE r.pno = t.pno
	 AND w.pno = t.pno
	 AND w.swift_code = b.bic

    UPDATE @tmp
       SET swift_bank 
         = CASE WHEN t.acc1 = 'XINTERNAL' THEN (SELECT opt_value FROM app_option WHERE opt_name = 'SSB_SWIFT_CODE')
           END
      FROM @tmp r, tra_fx_si t
     WHERE r.pno = t.pno

--��~���ڤH�W��
    UPDATE @tmp
       SET oppo_name 
         = ''

    UPDATE @tmp
       SET oppo_name
         = l.acc_name
      FROM @tmp r, @afos_client_local l
     WHERE r.pno = l.pno

--��s�״�/���ڤH��W
    UPDATE @tmp
       SET cp_bank 
         = ''

	UPDATE @tmp
       SET cp_bank
	   = b.cname
      FROM @tmp r, tra_fx_si t, cmn_broker b, afos_client_wss w
     WHERE r.pno = t.pno
	 AND w.pno = t.pno
	 AND w.swift_code = b.bic

    UPDATE @tmp
       SET cp_bank
	   = CASE WHEN t.acc1 = 'XINTERNAL' THEN (SELECT opt_value FROM app_option WHERE opt_name = 'sys_company_cname')
         END
      FROM @tmp r, tra_fx_si t
     WHERE r.pno = t.pno

--��s���L�M�׮֭㤽�帹

    UPDATE @tmp
       SET approv_no_flag 
         = ''
    UPDATE @tmp
       SET approv_no_flag 
         = CASE WHEN w.country = 'TW' AND l.cp_type = 1 THEN 'Y'
           END
      FROM @tmp r, @afos_client_local l ,afos_client_wss w 
     WHERE r.pno = l.pno
	 AND l.pno = w.pno

--��~���ڤH�Ȧ�b��
    UPDATE @tmp
       SET cp_bankacc 
         = ''

    UPDATE @tmp
       SET cp_bankacc
         = t.ben5
      FROM @tmp r, tra_fx_si t
     WHERE r.pno = t.pno

--forward_settle
 --   DECLARE @tra_fx TABLE
 --   (
 --       pno		 INT
	--  , trade_no VARCHAR (13)
	--  , parent   VARCHAR (13)
 --   )
 --   INSERT @tra_fx
 --   SELECT r.pno
	--	 , r.trade_no
	--FROM @tmp r, tra_fx t
	--WHERE r.trade_date = t.trade_date
	--AND t.product_type = 3 AND t.swap_sf = 2

    UPDATE @tmp
       SET forward_settle 
         = '1'

 --   UPDATE @tmp
 --      SET forward_settle
 --        = '3'
 --     FROM @tmp r, tra_fx t, tra_pair tp
	--WHERE r.trade_date = t.trade_date
	-- AND t.product_type = 3 AND t.swap_sf = 2
 --    AND t.trade_no = tp.child
	-- AND tp.parent = r.orig_trade_no
	-- AND tp.type = 2

--�g�J���G
    INSERT @result 
    SELECT pno
         , [date]
         , seq    
         , trade_no
         , value_date
         , cp_type
         , product_type
         , swap_sf
         , type
         , trade_status
         , orig_trade_no
		 , orig_trade_amt
		 , trade_type
		 , cb_trade_type                        
         , ccy                        
         , amt_in            
         , amt_out                   
         , exch_rate         
         , bal_amt           
         , note              
         , data_no        
         , country_source    
         , [class]           
         , class_detail      
         , kind_code         
         , forward_spl    
         , data_source       
         , data_kind         
         , oppo_name         
         , rem_type          
         , swift_bank        
         , 'M'               --data_source2  --���a M
         , bank              
         , bankacc           
         , cp_bank           
         , cp_bankacc      
		 , approv_no_flag  
		 , forward_settle
      FROM @tmp
      
    RETURN 
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant '[fn_UpdateCashFlowCb]', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\???\fn_GetPrivilegeTreeSource.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetPrivilegeTreeSource') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetPrivilegeTreeSource;
GO
/*------------------------------------------------------
版本：1.0.0
日期：2017-09-23
內容：產生使用者與群組畫面中權限 Tree 的資料源
-------------------------------------------------------*/
CREATE FUNCTION fn_GetPrivilegeTreeSource(@id VARCHAR(20), @key INT)
  RETURNS @result TABLE(
	  parentpos VARCHAR(15), itempos VARCHAR(15), itemcaption VARCHAR (50),
      runp BIT, selectp BIT, insertp BIT, updatep BIT, deletep BIT, 
	  lockp BIT, unlockp BIT, export BIT, setup BIT)
BEGIN

    INSERT @result
	SELECT p.itempos, m.itempos, m.itemcaption
         , ISNULL(f.runp, 0)
         , ISNULL(f.selectp, 0)
         , ISNULL(f.insertp, 0)
         , ISNULL(f.updatep, 0)
         , ISNULL(f.deletep, 0)
         , ISNULL(f.lockp, 0)
         , ISNULL(f.unlockp, 0)
         , ISNULL(f.export, 0)
         , ISNULL(f.setup, 0)
      FROM app_menu m
      LEFT JOIN
      (SELECT itempos FROM app_menu) p
        ON m.itempos LIKE p.itempos + '[A-Z]'
      LEFT JOIN fn_privilege(@id, @key) f
        ON m.itempos = f.itempos
	
	RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
	 EXEC sp_app_grant 'fn_GetPrivilegeTreeSource', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Function\???\fn_GetUserAndGroupReationTreeSource.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_GetUserAndGroupReationTreeSource') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_GetUserAndGroupReationTreeSource;
GO
/*------------------------------------------------------
版本：1.0.0
日期：2017-09-23
內容：產生使用者與群組畫面中從屬關係 Tree 的資料源
-------------------------------------------------------*/
CREATE FUNCTION fn_GetUserAndGroupReationTreeSource()
  RETURNS @result TABLE(pid VARCHAR(30), cid VARCHAR(30), parentkey INT, childkey INT, parentid VARCHAR(20), childid VARCHAR(20), name VARCHAR(40))
AS
BEGIN

    INSERT @result
	SELECT CAST(parentkey AS VARCHAR(3)) + '_'+ parentid
         , CAST(childkey AS VARCHAR(3)) + '_'+ childid
         , r.parentkey, r.childkey, r.parentid, r.childid, v.name 
	FROM app_userandrole r,
	(
		SELECT -1 AS [key], userid AS [id], username AS [name] 
		FROM app_user
		UNION ALL
		SELECT rolekey, roleid, rolename 
		FROM app_role
	) v
    WHERE r.childid = v.id AND r.childkey = v.[key]
    UNION ALL
    SELECT NULL, '0_ROOT', 9999, 0, NULL, 'ROOT', 'ROOT'
	
	RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
	 EXEC sp_app_grant 'fn_GetUserAndGroupReationTreeSource', 'ALL';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\sp_SetUserAccStatus.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_SetUserAccStatus]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
DROP PROCEDURE [dbo].[sp_SetUserAccStatus]
GO

/*---------------------------------
版本：1.0.1
日期：2017/11/20
內容：將執行紀錄寫至user_account_history_record

版本：1.0.0
日期：2017/11/15
內容：依據指定日期將使用者帳戶停權或刪除
---------------------------------*/
CREATE PROC sp_SetUserAccStatus
    @loguser	VARCHAR(20),
	@date		DATE
AS    

	DECLARE @user_table	TABLE
	( 
			user_acc VARCHAR(20), 
			deal_tp SMALLINT		--Option 904  1. Deactivated  4. Delete
	)

	 INSERT @user_table
	 SELECT userid, 1
	   FROM app_user
	  WHERE deactivated_date = @date AND enabled = 1
	  UNION 
	 SELECT userid, 2
	   FROM app_user
	  WHERE deletion_date = @date

	 UPDATE app_user
	    SET enabled = 0,
			logtime = GETDATE(),
			loguser = @loguser
	   FROM app_user AS real, @user_table AS ref
	  WHERE real.userid = ref.user_acc AND ref.deal_tp = 1

	 DELETE app_user
	   FROM app_user AS real, @user_table AS ref
	  WHERE real.userid = ref.user_acc AND ref.deal_tp = 4

	 INSERT user_account_history_record ([user], user_status, create_time, exec_type, loguser, logtime)
	 SELECT user_acc, deal_tp, GETDATE(), 2, 'ETL', GETDATE()
	   FROM app_user AS real, @user_table AS ref
	  WHERE real.userid = ref.user_acc

RETURN;

GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_SetUserAccStatus') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_SetUserAccStatus','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\??????sp_cash_dealend.sql"  
IF EXISTS ( SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[dbo].[sp_cash_dealend]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1 ) 
    DROP PROCEDURE [dbo].[sp_cash_dealend]
GO

/*---------------------------------
version    : 1.0.0
author     : Betsy
date       : 2017-11-07
description: 現金日結
---------------------------------*/
CREATE PROC sp_cash_dealend
    @pno            INT                   -- 契約序號
  , @date           SMALLDATETIME         -- 帳務日期
  , @native         INT                   -- 1: 國內; 2: 國外; 0: 國內外  
  , @assettp        INT                   -- 資產類型(0.所有 1.股票 2.債券 3.基金 4.定存 5.短票買賣斷6.附條件(RP))
  , @user           VARCHAR(20)           -- 用戶
  , @errmsg         NVARCHAR(500) OUTPUT  -- 錯誤訊息
AS 
SET NOCOUNT ON
SET XACT_ABORT ON

DECLARE @result INT
SET @result = 0
SET @errmsg = '';

BEGIN TRY 

----交易開始
BEGIN TRAN

    DECLARE @msg NVARCHAR(500) = ''
    DECLARE @is_ok INT = 1

    --更新現金異動
    EXEC @is_ok = sp_cash_flow_deal_end @pno, @date, @user, @msg OUTPUT
    IF @is_ok = 0
    BEGIN
        SET @errmsg = CONCAT(@errmsg, N'執行(更新 OSU 現金日結)發生錯誤!!', CHAR(13), CHAR(10), @msg)
        GOTO FINALLY;
    END

	--異動流程狀態為現金日結
	UPDATE pro_date
		SET excdate = @date
			, procuser = @user
			, proctime = GETDATE()
		WHERE (pno = @pno OR @pno = 0)
		AND proctp = 2 
		AND native = @native

COMMIT TRAN
----交易結束

END TRY
BEGIN CATCH
    GOTO ERR_HANDLER
END CATCH;

SELECT @result = 1
GOTO FINALLY

ERR_HANDLER:
    SET @result = 0;
    IF @@TRANCOUNT > 0 ROLLBACK TRAN;
    SELECT * FROM fn_error_info();
    RETURN @result;

FINALLY:
    IF @errmsg <> '' 
    BEGIN
        SET @result = 0;
        IF @@TRANCOUNT > 0 ROLLBACK TRAN;
    END
	ELSE
    RETURN @result;
GO

IF EXISTS ( SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id, 'IsProcedure') = 1 ) 
    EXEC sp_app_grant 'sp_cash_dealend', 'EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\??????sp_cash_dealend_back.sql"  
IF EXISTS ( SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[dbo].[sp_cash_dealend_back]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1 ) 
    DROP PROCEDURE [dbo].[sp_cash_dealend_back]
GO

/*---------------------------------
version    : 1.0.0
author     : Betsy
date       : 2017-11-08
description: 取消現金日結
---------------------------------*/
CREATE PROC sp_cash_dealend_back
    @pno            INT                   -- 契約序號
  , @date           SMALLDATETIME         -- 帳務日期
  , @native         INT                   -- 1: 國內; 2: 國外; 0: 國內外  
  , @assettp        INT                   -- 資產類型(0.所有 1.股票 2.債券 3.基金 4.定存 5.短票買賣斷6.附條件(RP))
  , @user           VARCHAR(20)           -- 用戶
  , @errmsg        NVARCHAR(500) OUTPUT   -- 錯誤訊息
AS 
SET NOCOUNT ON
SET XACT_ABORT ON

DECLARE @return INT
SET @return = 0
SET @errmsg = '';

BEGIN TRY--**程式開始

----交易開始
BEGIN TRAN
    
    --取得上一營業日
    DECLARE @last_bal_date SMALLDATETIME
    SELECT @last_bal_date = dbo.fn_GetWorkingDay(@date,'TWD',1,-1)
    
    --本日日結起始日
    DECLARE @begin_date SMALLDATETIME = DATEADD(D, 1, @last_bal_date)

		DELETE cb_cashflow
		 WHERE (pno = @pno OR @pno = 0) 
		   AND date = @date

		--異動流程狀態
		UPDATE pro_date
		   SET excdate = dbo.fn_GetWorkingDay(@date,'TWD',1,-1)
			 , procuser = @user
			 , proctime = GETDATE()
		 WHERE pno = @pno
		   AND proctp = 2 --現金日結
		   AND native = @native

COMMIT TRAN
----交易結束

END TRY--**程式結束
BEGIN CATCH
    GOTO ERR_HANDLER
END CATCH;

SELECT  @return = 1
GOTO FINALLY

ERR_HANDLER:
    SET @return = 0;
    IF @@TRANCOUNT > 0 ROLLBACK TRAN;
    SELECT * FROM fn_error_info();
    RETURN @return;

FINALLY:
    IF @errmsg <> '' 
    BEGIN
        SET @return = 0;
        IF @@TRANCOUNT > 0 ROLLBACK TRAN;
    END
    RETURN @return;
GO

IF EXISTS ( SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id, 'IsProcedure') = 1 ) 
    EXEC sp_app_grant 'sp_cash_dealend_back', 'EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\??????sp_cash_flow_deal_end.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_cash_flow_deal_end]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
    DROP PROCEDURE [dbo].[sp_cash_flow_deal_end]
GO

/*---------------------------------
version    : 1.0.0
author     : Betsy
date       : 2017-11-08
description: 
---------------------------------*/
CREATE PROC sp_cash_flow_deal_end
   @pno             INT                     -- 契約序號
 , @date            SMALLDATETIME           -- 帳務日期
 , @user            VARCHAR(20)             -- 用戶
 , @errmsg          NVARCHAR(500) OUTPUT    -- 錯誤訊息
AS

SET NOCOUNT ON
SET XACT_ABORT ON

DECLARE @result INT

--取得上一營業日
DECLARE @last_bal_date SMALLDATETIME
SELECT @last_bal_date = dbo.fn_GetWorkingDay(@date,'TWD',1,-1)

DECLARE @begin_date SMALLDATETIME
SELECT @begin_date = DATEADD(D, 1, @last_bal_date)

--tra_fx的 key 值, 以便更新過帳
DECLARE @tra_fx_key TABLE
(
    key_pno      INT
  , key_trade_no VARCHAR (40)
)
INSERT @tra_fx_key
SELECT pno, trade_no
  FROM tra_fx 
 WHERE (pno = @pno OR @pno = 0)
   AND trade_date BETWEEN @begin_date AND @date 

DECLARE @cash_flow tp_cash_flow

DECLARE @row_count INT = 0

--SPOT 賣出
SELECT @row_count = COUNT(*) FROM @cash_flow
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date , trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type
	 , value_date
	 , trade_type                                         
     , ccy_sell                                                --ccy_to
     , amt_sell                                                --amt_in
     , 0                                                       --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , swap_sf                                                 --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 1
   AND f.pno <> 0
   AND (f.status = '' OR f.status = 'F')

--SPOT 買入
SELECT @row_count = COUNT(*) FROM @cash_flow 
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date, trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type
	 , value_date
	 , trade_type                                        
     , ccy_buy                                                 --ccy_from
     , 0                                                       --amt_in
     , amt_buy                                                 --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 1
   AND f.pno <> 0
   AND (f.status = '' OR f.status = 'F')

--FORWARD 賣出
SELECT @row_count = COUNT(*) FROM @cash_flow
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date , trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type
	 , value_date
	 , trade_type                                         
     , ccy_sell                                                --ccy_to
     , amt_sell                                                --amt_in
     , 0                                                       --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 2
   AND f.pno <> 0
   AND (f.status = '' OR f.status = 'F')

--FORWARD 買入
SELECT @row_count = COUNT(*) FROM @cash_flow 
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date, trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type
	 , value_date
	 , trade_type                                        
     , ccy_buy                                                 --ccy_from
     , 0                                                       --amt_in
     , amt_buy                                                 --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 2
   AND f.pno <> 0
   AND (f.status = '' OR f.status = 'F')

--SWAP 賣出 SPOT
SELECT @row_count = COUNT(*) FROM @cash_flow
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date , trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type
	 , value_date
	 , trade_type                                         
     , ccy_sell                                                --ccy_to
     , amt_sell                                                --amt_in
     , 0                                                       --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 3
   AND f.pno <> 0
   AND f.swap_sf = 1
   AND (f.status = '' OR f.status = 'F')

--SWAP 買入 SPOT
SELECT @row_count = COUNT(*) FROM @cash_flow 
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date, trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type
	 , value_date
	 , trade_type                                        
     , ccy_buy                                                 --ccy_from
     , 0                                                       --amt_in
     , amt_buy                                                 --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 3
   AND f.pno <> 0
   AND f.swap_sf = 1
   AND (f.status = '' OR f.status = 'F')

--SWAP 賣出 FORWARD
SELECT @row_count = COUNT(*) FROM @cash_flow
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date , trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type
	 , value_date
	 , trade_type                                         
     , ccy_sell                                                --ccy_to
     , amt_sell                                                --amt_in
     , 0                                                       --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 3
   AND f.pno <> 0
   AND f.swap_sf = 2
   AND (f.status = '' OR f.status = 'F')

--SWAP 買入 FORWARD
SELECT @row_count = COUNT(*) FROM @cash_flow 
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date, trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type
	 , value_date
	 , trade_type                                        
     , ccy_buy                                                 --ccy_from
     , 0                                                       --amt_in
     , amt_buy                                                 --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 3
   AND f.pno <> 0
   AND f.swap_sf = 2
   AND (f.status = '' OR f.status = 'F')

--NDF 賣出
SELECT @row_count = COUNT(*) FROM @cash_flow
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date , trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type	 
	 , value_date
	 , trade_type                                         
     , ccy_sell                                                --ccy_to
     , amt_sell                                                --amt_in
     , 0                                                       --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 4
   AND f.pno <> 0
   AND (f.status = '' OR f.status = 'F')

--NDF 買入
SELECT @row_count = COUNT(*) FROM @cash_flow 
INSERT @cash_flow 
(
    pno, [date],exch_rate, seq, trade_no, product_type, value_date, trade_type
  , ccy, amt_in, amt_out, note
  , country_source, data_no, forward_spl, data_source, data_kind
  , bank, bankacc, cp_bank, cp_bankacc, swap_sf, orig_trade_no, type
)
SELECT f.pno
     , @date
	 , rate
     , @row_count + ROW_NUMBER() OVER(ORDER BY f.logtime ASC)    --seq
     , trade_no                                                --trade_no
	 , product_type	 
	 , value_date
	 , trade_type                                        
     , ccy_buy                                                 --ccy_from
     , 0                                                       --amt_in
     , amt_buy                                                 --amt_out
     , remark1                                                 --note
     , country                                                 --country_source
     , ''                                                      --data_no
     , ''                                                      --business_split
     , ''                                                      --data_source
     , ''                                                      --data_kind
     , ''                                                      --bank
     , ''                                                      --bankacc
     , ''                                                      --cp_bank
     , ''                                                      --cp_bankacc
	 , 0                                                       --swap_sf
	 , ''                                                      --orig_trade_no
	 , 0                                                       --type
  FROM tra_fx f, @tra_fx_key k, afos_client_wss a
 WHERE f.pno = k.key_pno
   AND f.pno = a.pno
   AND f.trade_no = k.key_trade_no
   AND f.product_type = 4
   AND f.pno <> 0
   AND (f.status = '' OR f.status = 'F')

--更新 bal_amt
UPDATE @cash_flow SET bal_amt = amt_in - amt_out

--更新央行申報選項
DECLARE @cb_cash_flow tp_cb_cash_flow
INSERT @cb_cash_flow
SELECT * FROM fn_UpdateCashFlowCb(@cash_flow, @pno, @date)
DECLARE @TranCounter INT;
SET @TranCounter = @@TRANCOUNT;
IF @TranCounter > 0 SAVE TRANSACTION sp_cash_flow_deal_end;
ELSE BEGIN TRAN

BEGIN TRY

	DELETE cb_cashflow
		WHERE (pno = @pno OR @pno = 0)
		AND date = @date 
	INSERT cb_cashflow
	SELECT *
			, ''              [putdate]
			, ''              [rcdate]
			, @user           [loguser]
			, GETDATE()       [logtime]
	FROM @cb_cash_flow

    IF @TranCounter = 0 COMMIT TRAN
END TRY

BEGIN CATCH
    GOTO ERR_HANDLER;
END CATCH

GOTO FINALLY;

ERR_HANDLER:
    SELECT @errmsg = errormessage FROM fn_error_info();
    IF @TranCounter = 0 ROLLBACK TRANSACTION;
    ELSE
    BEGIN
       IF XACT_STATE() <> -1
       BEGIN
           ROLLBACK TRANSACTION sp_cash_flow_deal_end;
       END
    END 

    SELECT @result = 0;
    RETURN @result;
    
FINALLY:
    SELECT @result = 1
    RETURN @result;
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_cash_flow_deal_end') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_cash_flow_deal_end','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\??????sp_dealstart.sql"  
IF EXISTS ( SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[dbo].[sp_dealstart]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1 ) 
    DROP PROCEDURE [dbo].[sp_dealstart]
GO

/*---------------------------------
version    : 1.0.0
author     : Betsy
date       : 2017-11-08
description: 交易日初
---------------------------------*/
CREATE PROC sp_dealstart
    @pno        INT                      -- 契約序號
  , @dt         SMALLDATETIME            -- 帳務日期
  , @native     INT                      -- 1: 國內; 2: 國外; 0: 國內外  
  , @assettp    INT                      -- 資產類型(0.所有 1.股票 2.債券 3.基金 4.定存 5.短票買賣斷6.附條件(RP))
  , @user       VARCHAR(20)              -- 用戶
  , @errmsg     NVARCHAR(500) OUTPUT     -- 錯誤訊息
AS 
SET NOCOUNT ON
SET XACT_ABORT ON

DECLARE @result INT
SET @result = 0
SET @errmsg = '';

BEGIN TRY

----交易開始
BEGIN TRAN

    -- 開帳
	IF NOT EXISTS ( SELECT pno FROM pro_date WITH ( NOLOCK ) WHERE pno = @pno ) 
	BEGIN
        --先用固定流程，應該考慮 ims_process_list
		INSERT pro_date VALUES ( @pno, 1, 0, 0, '', 0, 0 ) --國內外日初
		INSERT pro_date VALUES ( @pno, 2, 0, 0, '', 0, 1 ) --現金日結
	END
    --異動流程狀態
	UPDATE pro_date
		SET excdate = @dt, procuser = @user, proctime = GETDATE()
		WHERE pno = @pno 
		AND proctp = 1 
		AND native = @native

COMMIT TRAN
----交易結束
END TRY
BEGIN CATCH
    GOTO ERR_HANDLER
END CATCH;

SELECT @result = 1

GOTO FINALLY

ERR_HANDLER:
    SET @result = 0;
    IF @@TRANCOUNT > 0 ROLLBACK TRAN;
    SELECT * FROM fn_error_info();
    RETURN @result;

FINALLY:
    IF @errmsg <> '' 
    BEGIN
        SET @result = 0;
        IF @@TRANCOUNT > 0 ROLLBACK TRAN;

        SELECT @errmsg = @errmsg + CHAR(13) + N'日初作業失敗!';
    END
    RETURN @result;
GO

IF EXISTS ( SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id, 'IsProcedure') = 1 ) 
    EXEC sp_app_grant 'sp_dealstart', 'EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\??????sp_dealstart_back.sql"  
IF EXISTS ( SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[dbo].[sp_dealstart_back]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1 ) 
    DROP PROCEDURE [dbo].[sp_dealstart_back]
GO

/*---------------------------------
version    : 1.0.0
author     : Betsy
date       : 2017-11-08
description: 取消交易日初
---------------------------------*/
CREATE PROC sp_dealstart_back
    @pno        INT                   -- 契約序號
  , @dt         SMALLDATETIME         -- 帳務日期
  , @native     INT                   -- 1: 國內; 2: 國外; 0: 國內外
  , @assettp    INT                   -- 資產類型(0.所有 1.股票 2.債券 3.基金 4.定存 5.短票買賣斷6.附條件(RP))
  , @user       VARCHAR(20)           -- 用戶
  , @errmsg     NVARCHAR(500) OUTPUT  -- 錯誤訊息
AS 
SET NOCOUNT ON
SET XACT_ABORT ON

DECLARE @result INT
SET @result = 0
SET @errmsg = '';
BEGIN TRY
----交易開始
BEGIN TRAN
	DECLARE @last_end_dt DATETIME
    --上一日結日
	SELECT @last_end_dt = ISNULL(excdate, '') FROM pro_date WHERE pno = @pno AND proctp = 2
    
    --異動流程狀態
	UPDATE pro_date
		SET excdate = @last_end_dt, procuser = @user, proctime = GETDATE()
		WHERE pno = @pno 
		AND proctp = 1 
		AND native = @native

    --沒有做過日結，表示當天是第一天做日初
	IF @last_end_dt = ''
	BEGIN
		DELETE pro_date WHERE pno = @pno
	END

COMMIT TRAN
----交易結束
END TRY
BEGIN CATCH
    GOTO ERR_HANDLER
END CATCH;

SELECT @result = 1

GOTO FINALLY

ERR_HANDLER:
    SET @result = 0;
    IF @@TRANCOUNT > 0 ROLLBACK TRAN;
    SELECT * FROM fn_error_info();
    RETURN @result;

FINALLY:
    IF @errmsg <> '' 
    BEGIN
        SET @result = 0;
        IF @@TRANCOUNT > 0 ROLLBACK TRAN;
        
        SELECT @errmsg = @errmsg + CHAR(13) + CHAR(10) + N'取消日初作業失敗!';
    END
    RETURN @result;
GO

IF EXISTS ( SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id, 'IsProcedure') = 1 ) 
    EXEC sp_app_grant 'sp_dealstart_back', 'EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\??????sp_GetCbReport03.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_GetCbReport03]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
DROP PROCEDURE [dbo].[sp_GetCbReport03]
GO

/*---------------------------------
版本：1.0.0
日期：2015/7/16
內容：

INPUT
@date     : 作業日
---------------------------------*/
CREATE PROC sp_GetCbReport03
   @date SMALLDATETIME
AS
DELETE cb_report_03 WHERE date = @date

INSERT cb_report_03
SELECT @date,ROW_NUMBER() OVER (ORDER BY CURR),1,'',
CONVERT(VARCHAR(8),[DATA-DATE],112),BANK,[E-I-CODE],CURR,ITEM,
'00000000000000','00000000000000',
dbo.fn_NUMERIC([STORE-FORE-N]),dbo.fn_NUMERIC([STORE-FORE-C]),
dbo.fn_NUMERIC([NO-EXCHG-O-N]),dbo.fn_NUMERIC([NO-EXCHG-O-C]),
dbo.fn_NUMERIC([LINE-TOT-N]),dbo.fn_NUMERIC([LINE-TOT-C])
FROM fn_CbReport03(@date)

DECLARE @tmp TABLE(
	type			SMALLINT,
	[DATA-DATE]   	CHAR(8),
	[BANK]        	CHAR(2),
	[E-I-CODE]    	CHAR(1),
	[CURR]        	CHAR(3),
	[ITEM]        	CHAR(2),
	[EXCHG-NORM]  	NUMERIC(15,3),
	[EXCHG-CORR]  	NUMERIC(15,3),
	[STORE-FORE-N]	NUMERIC(15,3),
	[STORE-FORE-C]	NUMERIC(15,3),
	[NO-EXCHG-O-N]	NUMERIC(15,3),
	[NO-EXCHG-O-C]	NUMERIC(15,3),
	[LINE-TOT-N]  	NUMERIC(15,3),
	[LINE-TOT-C]  	NUMERIC(15,3))

INSERT @tmp		
SELECT 1,CONVERT(VARCHAR(8),[DATA-DATE],112),BANK,
[E-I-CODE],CURR,ITEM,[EXCHG-NORM],[EXCHG-CORR],
[STORE-FORE-N],[STORE-FORE-C],
[NO-EXCHG-O-N],[NO-EXCHG-O-C],
[LINE-TOT-N],[LINE-TOT-C] FROM fn_CbReport03(@date)

INSERT @tmp	
SELECT 0,[DATA-DATE],BANK,[E-I-CODE],CURR,ITEM,0,0,
dbo.fn_DENUMERIC([STORE-FORE-N]),dbo.fn_DENUMERIC([STORE-FORE-C]),
dbo.fn_DENUMERIC([NO-EXCHG-O-N]),dbo.fn_DENUMERIC([NO-EXCHG-O-C]),
dbo.fn_DENUMERIC([LINE-TOT-N]),dbo.fn_DENUMERIC([LINE-TOT-C])
FROM cb_report_03_wm WHERE date = @date

INSERT cb_report_03
SELECT @date,ROW_NUMBER() OVER (ORDER BY CURR),3,'',
[DATA-DATE],BANK,[E-I-CODE],CURR,ITEM,
'00000000000000','00000000000000',
dbo.fn_NUMERIC(SUM([STORE-FORE-N])),dbo.fn_NUMERIC(SUM([STORE-FORE-C])),
dbo.fn_NUMERIC(SUM([NO-EXCHG-O-N])),dbo.fn_NUMERIC(SUM([NO-EXCHG-O-C])),
dbo.fn_NUMERIC(SUM([LINE-TOT-N])),dbo.fn_NUMERIC(SUM([LINE-TOT-C]))
FROM @tmp GROUP BY [DATA-DATE],BANK,[E-I-CODE],CURR,ITEM

RETURN	
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_GetCbReport03','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\??????sp_UpdateCbWm01.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_UpdateCbWm01]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
DROP PROCEDURE [dbo].[sp_UpdateCbWm01]
GO

/*---------------------------------
版本：1.0.0
日期：2015/9/2
內容：

INPUT
@date     : 作業日
---------------------------------*/
CREATE PROC sp_UpdateCbWm01
   @date SMALLDATETIME
AS
DECLARE @i INT;
SELECT @i = ISNULL(MAX(CAST([SER-NO] AS INT)),0)
  FROM cb_report_01
 WHERE date = @date
   
DECLARE @tmp TABLE
(
	[SER-NO]	CHAR(5),
	[DATA-NO]	CHAR (12),
	[date]		SMALLDATETIME,
	seq			INT
)

INSERT @tmp
SELECT REPLACE(STR ( ROW_NUMBER() OVER (ORDER BY [DATA-NO])+@i,5),' ','0') AS SERNO,
	   [DATA-NO], date, seq
  FROM cb_report_01_wm 
 WHERE date = @date
 
UPDATE cb_report_01_wm 
   SET [SER-NO] = t.[SER-NO] 
  FROM cb_report_01_wm a, @tmp t  
 WHERE a.date = t.date AND a.seq = t.seq

/*UPDATE cb_report_01_wm 
   SET [SER-NO] = 
   (SELECT t.[SER-NO] FROM @tmp t
   WHERE [cb_report_01_wm].seq = t.seq)
   WHERE date = '2015-2-2'*/
RETURN	
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_UpdateCbWm01','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\??????sp_UpdateCbWm02.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_UpdateCbWm02]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
DROP PROCEDURE [dbo].[sp_UpdateCbWm02]
GO

/*---------------------------------
版本：1.0.0
日期：2015/9/2
內容：

INPUT
@date     : 作業日
---------------------------------*/
CREATE PROC sp_UpdateCbWm02
   @date SMALLDATETIME
AS
DECLARE @i INT;
SELECT @i = ISNULL(MAX(CAST([SER-NO] AS INT)),0)
  FROM cb_report_02
 WHERE date = @date
   
DECLARE @tmp TABLE
(
	[SER-NO]	CHAR(5),
	[DATA-NO]	CHAR (12),
	[date]		SMALLDATETIME,
	seq			INT
)

INSERT @tmp
SELECT REPLACE(STR ( ROW_NUMBER() OVER (ORDER BY [DATA-NO])+@i,5),' ','0') AS SERNO,
	   [DATA-NO], date, seq
  FROM cb_report_02_wm 
 WHERE date = @date
 
UPDATE cb_report_02_wm 
   SET [SER-NO] = t.[SER-NO] 
  FROM cb_report_02_wm a, @tmp t  
 WHERE a.date = t.date AND a.seq = t.seq

/*UPDATE cb_report_02_wm 
   SET [SER-NO] = 
   (SELECT t.[SER-NO] FROM @tmp t
   WHERE [cb_report_02_wm].seq = t.seq)
   WHERE date = '2015-2-2'*/
RETURN	
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_UpdateCbWm02','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\???\sp_DoExportInfomation.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_DoExportInfomation]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
DROP PROCEDURE [dbo].[sp_DoExportInfomation]
GO

/*---------------------------------
版本：1.0.0
日期：2017/09/18
內容：匯出各種權限資訊
---------------------------------*/
CREATE PROC sp_DoExportInfomation
    @infomation SMALLINT
AS    

IF @infomation = 1--使用者資訊
BEGIN
    SELECT r.parentid AS [Group],
       r.childid AS [User],
       CASE u.enabled WHEN 1 THEN 'V' ELSE '' END AS [Activated],
       CASE u.deactivated_date WHEN '' THEN '' ELSE CONVERT(CHAR(10), u.deactivated_date, 111) END AS [Deactivation Date],
       CASE u.deletion_date WHEN '' THEN '' ELSE CONVERT(CHAR(10), u.deletion_date, 111) END AS [Deletion Date]
    FROM app_user u, app_userandrole r
    WHERE u.userid = r.childid AND r.childkey = -1
    ORDER BY r.parentid, r.childid
END

IF @infomation = 2--群組權限
BEGIN
    SELECT r.roleid AS [Group], 
           m.itemcaption AS [Menu Item],
           CASE p.runp WHEN 1 THEN 'V' ELSE '' END AS [Execute],
           CASE p.insertp WHEN 1 THEN 'V' ELSE '' END AS [Insert],
           CASE p.updatep WHEN 1 THEN 'V' ELSE '' END AS [Modify],
           CASE p.deletep WHEN 1 THEN 'V' ELSE '' END AS [Delete],
           CASE p.lockp WHEN 1 THEN 'V' ELSE '' END AS [Lock],
           CASE p.unlockp WHEN 1 THEN 'V' ELSE '' END AS [Unlock],
           CASE p.export WHEN 1 THEN 'V' ELSE '' END AS [Export],
           CASE p.setup WHEN 1 THEN 'V' ELSE '' END AS [Setup]
    FROM app_role r 
    CROSS JOIN app_menu m    
    LEFT JOIN app_privilege p 
    ON p.itempos = m.itempos
    AND r.rolekey = p.clientkey
    ORDER BY r.roleid, m.itempos
END

RETURN;

GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_DoExportInfomation') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_DoExportInfomation','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\???\sp_DoLogPrivilege.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_DoLogPrivilege]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
DROP PROCEDURE [dbo].[sp_DoLogPrivilege]
GO

/*---------------------------------
版本：1.0.0
日期：2017/09/18
內容：紀錄權限異動
---------------------------------*/
CREATE PROC sp_DoLogPrivilege
    @privilege tp_Privilege READONLY,
    @id        VARCHAR(20), 
    @key       INT,   
    @loguser   VARCHAR(20)
AS    
      
  MERGE app_privilege AS T
  USING @privilege AS S
  ON (T.itempos = S.itempos AND T.clientid = @id AND T.clientkey = @key) 
  WHEN NOT MATCHED
    THEN INSERT
    (
      itempos, clientid, clientkey, runp, selectp, insertp, updatep, 
      deletep, printp, lockp, unlockp, export, setup, loguser, logtime
    ) 
    VALUES
    (
      S.itempos, @id, @key, S.runp, S.selectp, S.insertp, 
      S.updatep, S.deletep, S.printp, S.lockp, S.unlockp, 
      S.export, S.setup, @loguser, GETDATE()
    )
    WHEN MATCHED 
    THEN UPDATE SET     
    T.runp = S.runp, T.selectp = S.selectp, T.insertp = S.insertp, 
    T.updatep = S.updatep, T.deletep = S.deletep, T.printp = S.printp, 
    T.lockp = S.lockp, T.unlockp = S.unlockp, T.export = S.export, 
    T.setup = S.setup, T.loguser = @loguser, T.logtime = GETDATE();

    --寫 log
    DECLARE @max_no VARCHAR(10)
    SELECT @max_no = CAST(ISNULL(MAX(changedno), 0) + 1 AS VARCHAR(10))
    FROM app_privilege_log

    DECLARE @no VARCHAR(10)
    SELECT @no = REPLICATE('0', 10 - LEN(@max_no)) + @max_no;
    
    INSERT app_privilege_log
    SELECT @no, @key, @id, p.itempos, m.itemcaption, 0, 
           p.runp, p.selectp, p.insertp, p.updatep, 
           p.deletep, p.printp, p.lockp, p.unlockp, 
           p.export, p.setup, @loguser, GETDATE()
    FROM @privilege p, app_menu m
    WHERE p.itempos = m.itempos

    DELETE app_privilege 
    WHERE runp | insertp | updatep | deletep | lockp 
        | unlockp | export | setup = 0
    
  RETURN;

GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_DoLogPrivilege') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_DoLogPrivilege','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\???\sp_DoLogUserAccount.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_DoLogUserAccount]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
DROP PROCEDURE [dbo].[sp_DoLogUserAccount]
GO

/*---------------------------------
版本：1.0.0
日期：2017/09/18
內容：紀錄 User Account 異動
---------------------------------*/
CREATE PROC sp_DoLogUserAccount
    @user     VARCHAR(20),
    @status   SMALLINT,
    @type     SMALLINT,
    @loguser  VARCHAR(20)
AS    

IF @status = 3 --新增
BEGIN
    INSERT user_account_history_record 
    SELECT @user, @status, GETDATE(), @type, @loguser, GETDATE()
END
ELSE
BEGIN
  DECLARE @create_time DATETIME
  SELECT @create_time = MAX(create_time) FROM user_account_history_record 
  WHERE [user] = @user AND user_status = 3

  IF EXISTS
  (
    SELECT 1 FROM user_account_history_record 
    WHERE [user] = @user AND user_status = @status AND create_time = @create_time
  )
  BEGIN
      UPDATE user_account_history_record
      SET exec_type = @type, loguser = @loguser, logtime = GETDATE()
      WHERE [user] = @user AND user_status = @status AND create_time = @create_time
  END
  ELSE
  BEGIN
      INSERT user_account_history_record 
      SELECT @user, @status, @create_time, @type, @loguser, GETDATE()
  END  
END    
  RETURN;

GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_DoLogUserAccount') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_DoLogUserAccount','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\StoredProcedure\???\sp_DoLogUserGroupRelation.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[sp_DoLogUserGroupRelation]') AND OBJECTPROPERTY(id, N'IsProcedure') = 1)
DROP PROCEDURE [dbo].[sp_DoLogUserGroupRelation]
GO

/*---------------------------------
版本：1.0.0
日期：2017/09/18
內容：紀錄 User/ Group 從屬關係異動
---------------------------------*/
CREATE PROC sp_DoLogUserGroupRelation
    @relation tp_UserAndRoleRelation READONLY,
    @status   SMALLINT,    
    @loguser  VARCHAR(20)
AS    

IF @status = 1 --新增使用者
BEGIN
    INSERT app_userandrole 
    SELECT *, @loguser, GETDATE() FROM @relation

    INSERT app_user_transfer_log 
    SELECT childid, 1, parentid, parentkey, @loguser, GETDATE() FROM @relation
END

IF @status = 3 --刪除使用者
BEGIN
    DELETE app_userandrole
    FROM app_userandrole a, @relation r
    WHERE a.childid = r.childid AND a.childkey = r.childkey

    DELETE app_user_transfer_log 
    FROM app_user_transfer_log l, @relation r
    WHERE l.userid = r.childid
END

IF @status = 4  --新增群組
BEGIN
    INSERT app_userandrole 
    SELECT *, @loguser, GETDATE() FROM @relation 
END

IF @status = 6 --刪除群組
BEGIN
    DELETE app_userandrole
    FROM app_userandrole a, @relation r
    WHERE a.childid = r.childid AND a.childkey = r.childkey
    
    INSERT app_user_transfer_log
    SELECT l.*, r.parentid, r.parentkey, @loguser, GETDATE()
    FROM (
           SELECT userid, MAX(transfer_index) + 1 AS idx 
           FROM app_user_transfer_log
           GROUP BY userid
         ) l,
         (
           SELECT a.childid, r.parentid, r.parentkey
           FROM app_userandrole a, @relation r
           WHERE a.childkey = -1 AND a.parentid = r.childid AND a.parentkey = r.childkey
         ) r
     WHERE l.userid = r.childid

    UPDATE app_userandrole
    SET parentid = r.parentid, parentkey = r.parentkey
      , loguser = @loguser, logtime = GETDATE()
    FROM app_userandrole a, @relation r
    WHERE a.parentid = r.childid AND a.parentkey = r.childkey  
END

IF @status = 7--修改從屬關係
BEGIN   
    UPDATE app_userandrole
    SET parentid = r.parentid, parentkey = r.parentkey
      , loguser = @loguser, logtime = GETDATE()
    FROM app_userandrole a, @relation r
    WHERE a.childid = r.childid AND a.childkey = r.childkey

    INSERT app_user_transfer_log
    SELECT a.*, r.parentid, r.parentkey, @loguser, GETDATE()
    FROM (
           SELECT userid, MAX(transfer_index) + 1 AS idx 
           FROM app_user_transfer_log
           GROUP BY userid
         ) a,
         (
           SELECT * FROM @relation WHERE childkey = -1
         ) r
     WHERE a.userid = r.childid   
END

RETURN;

GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_DoLogUserGroupRelation') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_DoLogUserGroupRelation','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\sp_desc.sql"  
if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[sp_desc]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)
drop procedure [dbo].[sp_desc]
GO

/*---------------------------------
版本：1.1.2
日期：2014-12-01
功用：修正 NVARCHAR 顯示的長度
版本：1.1.1
日期：2014-02-12
功用：可顯示 key 值。 
版本：1.1.0
日期：2013-10-30 
功用：List Columns AND Types for USER_TABLE, VIEW, SQL_TABLE_VALUED_FUNCTION and USER_DEFINED_TYPE
     GET Return Data Type for Scalar Function
版本：1.0.0
日期：2013-10-23 
功用：同在 oracle 下 desc
---------------------------------*/
CREATE PROC sp_desc 
	@name VARCHAR(255) 
AS

SET nocount ON
SET xact_abort ON

DECLARE @ret int
SELECT @ret=0

BEGIN TRY
	--**程式開始
	DECLARE @sp_columns TABLE(
			TABLE_QUALIFIER sysname, TABLE_OWNER sysname, TABLE_NAME sysname, COLUMN_NAME sysname,
			DATA_TYPE smallint, [TYPE_NAME] sysname, [PRECISION] int, [LENGTH] int, SCALE smallint,
			RADIX smallint, NULLABLE smallint, REMARKS varchar(254), COLUMN_DEF nvarchar(4000),
			SQL_DATA_TYPE smallint, SQL_DATETIME_SUB smallint, CHAR_OCTET_LENGTH int, ORDINAL_POSITION int,
			IS_NULLABLE varchar(254), SS_DATA_TYPE tinyint)
			
	DECLARE @sproc_columns TABLE(
			PROCEDURE_QUALIFIER sysname, PROCEDURE_OWNER sysname, [PROCEDURE_NAME] nvarchar(134),
			COLUMN_NAME sysname, COLUMN_TYPE smallint, DATA_TYPE smallint, [TYPE_NAME] sysname,
            [PRECISION] int, [LENGTH] int, [SCALE] smallint, RADIX smallint, NULLABLE smallint,
            REMARKS varchar(254), COLUMN_DEF nvarchar(4000), SQL_DATA_TYPE smallint, 
            SQL_DATETIME_SUB smallint, CHAR_OCTET_LENGTH int, ORDINAL_POSITION int, 
            IS_NULLABLE varchar(254), SS_DATA_TYPE tinyint)		
				
	DECLARE @type_desc NVARCHAR(60);
	SELECT @type_desc = type_desc FROM sys.objects WHERE name = @name;
	
	IF @type_desc = 'SQL_SCALAR_FUNCTION'
	BEGIN
		INSERT @sproc_columns
		EXEC sys.sp_sproc_columns @name
		
		SELECT [TYPE_NAME] +		
			   CASE UPPER([TYPE_NAME]) WHEN 'NUMERIC' THEN ' (' + CAST([PRECISION] AS VARCHAR) + ',' + CAST([SCALE] AS VARCHAR) + ')'
									   WHEN 'CHAR' THEN ' (' + CAST([LENGTH] AS VARCHAR) + ')'
									   WHEN 'VARCHAR' THEN ' (' + CAST([LENGTH] AS VARCHAR) + ')'
									   WHEN 'NVARCHAR' THEN ' (' + CAST([LENGTH]/2 AS VARCHAR) + ')'					  
									   ELSE '' END AS [Type]
		FROM @sproc_columns
		WHERE COLUMN_NAME = '@RETURN_VALUE'
				
	END
	
	ELSE IF @type_desc = 'SQL_TABLE_VALUED_FUNCTION' OR @type_desc = 'VIEW' 
	BEGIN
		INSERT @sp_columns 
		EXEC sp_columns @name
		
		SELECT COLUMN_NAME AS Name,
			   UPPER([TYPE_NAME]) +
			   CASE UPPER([TYPE_NAME]) 
			      WHEN 'NUMERIC' THEN ' (' + CAST([PRECISION] AS VARCHAR) + ',' + CAST([SCALE] AS VARCHAR) + ')'
				  WHEN 'CHAR' THEN ' (' + CAST([LENGTH] AS VARCHAR) + ')'
				  WHEN 'VARCHAR' THEN ' (' + CAST([LENGTH] AS VARCHAR) + ')'
				  WHEN 'NVARCHAR' THEN ' (' + CAST([LENGTH]/2 AS VARCHAR) + ')'
				  ELSE '' END AS [Type]
		FROM @sp_columns
			
	END
	
	ELSE IF @type_desc = 'USER_TABLE'      	   
	BEGIN
		INSERT @sp_columns 
		EXEC sp_columns @name
				
		DECLARE @returnTable TABLE([Key] CHAR(1), Name VARCHAR(40), [Type] VARCHAR(50), [Cname] VARCHAR(40), [Options] VARCHAR(MAX))

		INSERT @returnTable
		SELECT '', COLUMN_NAME, 
			   UPPER([TYPE_NAME]) +
			   CASE UPPER([TYPE_NAME]) 
				  WHEN 'NUMERIC' THEN ' (' + CAST([PRECISION] AS VARCHAR) + ',' + CAST([SCALE] AS VARCHAR) + ')'									 
				  WHEN 'CHAR' THEN ' (' + CAST([LENGTH] AS VARCHAR) + ')'				  
				  WHEN 'VARCHAR' THEN ' (' + CAST([LENGTH] AS VARCHAR) + ')'
				  WHEN 'NVARCHAR' THEN ' (' + CAST([LENGTH] AS VARCHAR) + ')'
				  ELSE '' END, 
			   '', ''		   
		FROM @sp_columns
		
		UPDATE @returnTable
		SET [Key] = 'V' 
		FROM @returnTable r
		WHERE EXISTS (
		    SELECT * FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE i
            WHERE OBJECTPROPERTY(OBJECT_ID(i.CONSTRAINT_NAME), 'IsPrimaryKey') = 1
            AND i.TABLE_NAME = @name 
            AND i.COLUMN_NAME = r.Name)
	    
		UPDATE @returnTable 
		SET [Cname] = a.ctitle,
			[Options] = CASE [Type] WHEN 'SMALLINT' THEN CAST(a.opt_type AS VARCHAR)
						ELSE '' END
		FROM @returnTable r, app_table_field a
		WHERE a.tablename  = @name AND
			  a.fieldname = r.Name;

		DECLARE @item VARCHAR(30), @option VARCHAR(MAX), @comments VARCHAR(MAX)
		DECLARE #c1 CURSOR FAST_FORWARD FOR (SELECT DISTINCT Options FROM @returnTable WHERE Options <> '')
		OPEN #c1
			FETCH NEXT FROM #c1 INTO @option
			WHILE @@fetch_status = 0
			BEGIN		
				SET @comments = ''		
				DECLARE #c2 CURSOR FAST_FORWARD FOR (SELECT name FROM app_table_field_option_item WHERE opt_no = @option)
				OPEN #c2
				FETCH NEXT FROM #c2 INTO @item
				WHILE @@fetch_status = 0
				BEGIN
					SET @comments = @comments + @item + ' '
					FETCH NEXT FROM #c2 INTO @item
				END	
				CLOSE #c2
				DEALLOCATE #c2
				UPDATE @returnTable SET Options = Options + '\' + @comments WHERE Options = @option			

				FETCH NEXT FROM #c1 INTO @option
			END
		CLOSE #c1
		DEALLOCATE #c1

		SELECT * FROM @returnTable	 
	END
	ELSE
	BEGIN
		DECLARE @isType BIT
		IF EXISTS (SELECT 1 FROM sys.table_types WHERE name = @name) SELECT 1
		ELSE SELECT 0
		
		IF @isType = 1		
		BEGIN
			SELECT c.name AS Name,
			       UPPER(t.name) +
				   CASE UPPER(t.name) WHEN 'NUMERIC' THEN ' (' + CAST(c.[precision] AS VARCHAR) + ',' + CAST(c.scale AS VARCHAR) + ')'
									  WHEN 'CHAR' THEN ' (' + CAST(c.max_length AS VARCHAR) + ')'
									  WHEN 'VARCHAR' THEN ' (' + CAST(c.max_length AS VARCHAR) + ')'
									  WHEN 'NVARCHAR' THEN ' (' + CAST(c.max_length/2 AS VARCHAR) + ')'
									  ELSE '' END AS [Type] 
			FROM sys.table_types as tt, sys.columns as c, sys.types as t 
			WHERE tt.type_table_object_id = c.object_id 
			AND c.system_type_id = t.system_type_id 
			AND tt.name = @name
			ORDER BY c.column_id
		END
		ELSE SELECT 'NOT VALID QUERY NAME' AS [MESSAGE]
	END
	--**程式結束
	
END TRY

BEGIN CATCH
	GOTO err_handler		
END CATCH;

SELECT @ret=1
GOTO finally
  	
err_handler:
	select @ret=0;
	if @@TRANCOUNT > 0 rollback tran;
	select * from fn_error_info();
	return @ret;

finally:
	return @ret;
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_desc','EXEC';
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\fn\fn_allUserPrivilege.sql"  
if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[fn_allUserPrivilege]') and xtype in (N'FN', N'IF', N'TF'))
drop function [dbo].[fn_allUserPrivilege]
GO
/*---------------------------------
版本 : 1.0.1
日期 : 2013-07-19
內容 : 全部使用者或群組所有權限
參數 : 

INPUT
@opt     : -1 使用者, 0 使用者跟群組, 1 群組
@showall : 是否顯示所有功能欄位。    
---------------------------------*/

CREATE FUNCTION fn_allUserPrivilege(@opt int, @showall bit)
RETURNS @privilege table(clientid VARCHAR(20), clientkey INT, itemCaption VARCHAR(50), itempos varchar(15), runp bit, selectp bit, insertp bit, 
updatep bit, deletep bit, printp bit, lockp bit, unlockp bit, export bit, setup bit)
AS
  BEGIN
  	DECLARE @key INT;
	DECLARE @id VARCHAR(20);
		
	IF @opt >= 0
	BEGIN		
		DECLARE c1 CURSOR FAST_FORWARD FOR SELECT DISTINCT rolekey, roleid FROM app_role
		OPEN c1
		FETCH NEXT FROM c1 INTO @key, @id
		IF @showall = 1
		BEGIN
			WHILE @@FETCH_STATUS = 0
			BEGIN
				INSERT INTO @privilege			
				SELECT @id, @key, itemcaption, itempos, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 FROM app_menu			
				UPDATE @privilege 
				SET runp = a.runp , selectp = a.selectp, insertp = a.insertp, updatep = a.updatep, 
				deletep = a.deletep, printp = a.printp, lockp = a.lockp, unlockp = a.unlockp, 
				export = a.export, setup = a.setup
				FROM dbo.fn_privilege(@id, @key) a, @privilege b
				WHERE b.clientid = @id AND b.clientkey = @key AND a.itempos = b.itempos			
				FETCH NEXT FROM c1 INTO @key, @id
			END
		END
		ELSE
		BEGIN
			WHILE @@FETCH_STATUS = 0
			BEGIN
				INSERT INTO @privilege
				SELECT @id, @key, itemcaption, a.* 
				FROM dbo.fn_privilege(@id, @key) a, app_menu b
				WHERE a.itempos = b.itempos
				FETCH NEXT FROM c1 INTO @key, @id
			END
		END
		CLOSE c1
		DEALLOCATE c1	
	END    		
	IF @opt <= 0
	BEGIN		
		DECLARE c2 CURSOR FAST_FORWARD FOR SELECT DISTINCT userid FROM app_user
		OPEN c2
		FETCH NEXT FROM c2 INTO @id
		IF @showall = 1
		BEGIN
			WHILE @@FETCH_STATUS = 0
			BEGIN
				INSERT INTO @privilege				
				SELECT @id, -1, itemcaption, itempos, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 FROM app_menu				
				UPDATE @privilege 
				SET runp = a.runp , selectp = a.selectp, insertp = a.insertp, updatep = a.updatep, 
				deletep = a.deletep, printp = a.printp, lockp = a.lockp, unlockp = a.unlockp, 
				export = a.export, setup = a.setup
				FROM dbo.fn_privilege(@id, -1) a, @privilege b
				WHERE b.clientid = @id AND b.clientkey = -1 AND a.itempos = b.itempos				
				FETCH NEXT FROM c2 INTO @id
			END
		END
		ELSE
		BEGIN
			WHILE @@FETCH_STATUS = 0
			BEGIN
				INSERT INTO @privilege
				SELECT @id, -1, itemcaption, a.* 
				FROM dbo.fn_privilege(@id, -1) a, app_menu b
				WHERE a.itempos = b.itempos				
				FETCH NEXT FROM c2 INTO @id
			END
		END
		CLOSE c2
		DEALLOCATE c2
	END
	IF @showall = 0
	BEGIN
		DELETE @privilege WHERE runp = 0 AND selectp = 0 AND insertp = 0 AND updatep = 0 AND deletep = 0 
								AND printp = 0 AND lockp = 0 AND unlockp = 0 AND export = 0 AND setup = 0
	END
    RETURN
  END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_allUserPrivilege', 'all'
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\fn\fn_error_info.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('fn_error_info') AND xtype IN ('FN','IF','TF'))
   DROP FUNCTION fn_error_info;
GO

/*---------------------------------
 版本 : 1.0.0
 
 日期 : 2011-11-07 (1.0.0)
 內容 : 顯示 stored procedure 的錯誤訊息 (SQL 2000不適用)
---------------------------------*/
CREATE FUNCTION [dbo].[fn_error_info]()
RETURNS @ret TABLE(errornumber int, severity int, errorstate int, errorprocedure varchar(50), 
errorline int, errormessage varchar(500))
AS
BEGIN
	insert into @ret
	select 
        ERROR_NUMBER() AS ErrorNumber,
        ERROR_SEVERITY() AS ErrorSeverity,
        ERROR_STATE() as ErrorState,
        ERROR_PROCEDURE() as ErrorProcedure,
        ERROR_LINE() as ErrorLine,
        ERROR_MESSAGE() as ErrorMessage;
	
	return
END

GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_error_info', 'ALL';
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\fn\fn_GetSingleUserPrivilege.sql"  
if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[fn_GetSingleUserPrivilege]') and xtype in (N'FN', N'IF', N'TF'))
drop function [dbo].[fn_GetSingleUserPrivilege]
GO
/*---------------------------------
版本 : 1.0.0
日期 : 2015-07-13
內容 : 擷取單一使用者所有權限，來判斷使用者的權限異動情形
參數 : 

INPUT  @clientid varchar(20)
---------------------------------*/

CREATE FUNCTION fn_GetSingleUserPrivilege(@clientid varchar(20))
RETURNS @privilege TABLE
(
    clientid  VARCHAR(20)
  , clientkey INT
  , itempos   VARCHAR(15)
  , runp      BIT
  , selectp   BIT
  , insertp   BIT
  , updatep   BIT
  , deletep   BIT
  , printp    BIT
  , lockp     BIT
  , unlockp   BIT
  , export    BIT
  , setup     BIT
)
AS
BEGIN
  
    INSERT INTO @privilege
    SELECT @clientid
         , -1
         , a.itempos
         , ISNULL(b.runp, 0)
         , ISNULL(b.selectp, 0)
         , ISNULL(b.insertp, 0)
         , ISNULL(b.updatep, 0)
         , ISNULL(b.deletep, 0)
         , ISNULL(b.printp, 0)
         , ISNULL(b.lockp, 0)
         , ISNULL(b.unlockp, 0)
         , ISNULL(b.export, 0)
         , ISNULL(b.setup, 0)
    FROM app_menu a
    LEFT JOIN dbo.fn_privilege(@clientid, -1) b
    ON a.itempos = b.itempos

    RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_GetSingleUserPrivilege', 'all'
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\fn\fn_menu_priv.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[fn_menu_priv]') AND xtype IN (N'FN', N'IF', N'TF'))
DROP FUNCTION [dbo].[fn_menu_priv]
GO

/*---------------------------------
版本 : 1.0.0
日期 : 2015-06-30
內容 : 新增 export, setup 欄位

版本 : 1.0.0
日期 : 2014-07-22
內容 : 使用者或群組所有選單權限
---------------------------------*/

CREATE FUNCTION fn_menu_priv(@clientid VARCHAR(20), @clientkey INT)
RETURNS @privilege TABLE
(
  itempos VARCHAR(15), pkgname VARCHAR(30), itemid INT, typename VARCHAR(50)
, runp BIT, selectp BIT, insertp BIT, updatep BIT, deletep BIT, printp BIT
, lockp BIT, unlockp BIT, export BIT, setup BIT
)
AS
BEGIN
IF @clientkey = -99 --default admin
BEGIN
INSERT INTO @privilege
    SELECT itempos, pkgname, itemid, typename
         , 1 AS runp, 1 AS selectp, 1 AS insertp, 1 AS updatep, 1 AS deletep, 1 AS printp
         , 1 AS lockp, 1 AS unlockp, 1 AS export, 1 AS setup
    FROM app_menu
    ORDER BY itempos
END
ELSE
BEGIN
    INSERT INTO @privilege
        SELECT a.itempos, a.pkgname, a.itemid, a.typename
      , ISNULL(b.runp, 0) AS runp
      , ISNULL(b.selectp, 0) AS selectp
      , ISNULL(b.insertp, 0) AS insertp
      , ISNULL(b.updatep, 0) AS updatep
      , ISNULL(b.deletep, 0) AS deletep
      , ISNULL(b.printp, 0) AS printp
      , ISNULL(b.lockp, 0) AS lockp
      , ISNULL(b.unlockp, 0) AS unlockp
      , ISNULL(b.export, 0) AS export
      , ISNULL(b.setup, 0) AS setup
        FROM app_menu a
        LEFT JOIN dbo.fn_privilege(@clientid, @clientkey) b
        on a.itempos =b.itempos
        ORDER BY a.itempos
    END
    RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_menu_priv', 'all'
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\fn\fn_parent.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[fn_parent]') AND xtype IN (N'FN', N'IF', N'TF'))
DROP FUNCTION [dbo].[fn_parent]
GO

/*
版本：1.0.0
日期：2014/07/22
內容：使用者或群組的父代群組
*/

CREATE FUNCTION fn_parent(@childid varchar(20), @childkey int)
RETURNS @parent TABLE(parentid varchar(20), parentkey int, group_level int)
AS

  BEGIN
    DECLARE @parentid varchar(20), @parentkey int, @group_level int 
	
	SELECT @parentid = parentid, @parentkey = parentkey FROM app_userandrole WHERE childid = @childid AND childkey = @childkey
	SELECT @group_level = 0;
	
	WHILE (@parentkey > 0)
	BEGIN
		INSERT INTO @parent VALUES(@parentid, @parentkey, @group_level);
		SELECT @childid = @parentid, @childkey = @parentkey, @group_level = @group_level + 1
		SELECT @parentid = parentid, @parentkey = parentkey FROM app_userandrole WHERE childid = @childid AND childkey = @childkey
    END

	INSERT INTO @parent VALUES(@parentid, @parentkey, @group_level);
    
    RETURN
  END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_parent', 'all'
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\fn\fn_permission.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[fn_permission]') AND xtype IN (N'FN', N'IF', N'TF'))
DROP FUNCTION [dbo].[fn_permission]
GO

/*
版本：1.0.0
日期：2014/07/22
內容：使用者或群組所有特定權限
*/

CREATE FUNCTION fn_permission(@clientid varchar(20), @clientkey int, @pno int)
RETURNS @permission table(pno int, itempos varchar(15), selectp bit, insertp bit, 
	updatep bit, deletep bit, printp bit, lockp bit, unlockp bit, export bit)
AS
BEGIN	
	INSERT INTO @permission
		
		SELECT a.pno, a.itempos, a.selectp, a.insertp, a.updatep, a.deletep, a.printp, a.lockp, a.unlockp, a.export 
		FROM app_permission a 
		INNER JOIN app_menu b ON a.itempos=b.itempos 
		WHERE b.itemcaption <> '-' AND a.userid=@clientid AND (a.pno=@pno OR @pno=0)

RETURN
END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_permission', 'all'
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\fn\fn_privilege.sql"  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = object_id(N'[dbo].[fn_privilege]') AND xtype IN (N'FN', N'IF', N'TF'))
DROP FUNCTION [dbo].[fn_privilege]
GO
/*---------------------------------                                                         
版本 : 1.0.0
日期 : 2014/07/22
內容 : 使用者或群組所有權限
---------------------------------*/

CREATE FUNCTION fn_privilege(@clientid varchar(20), @clientkey int)
RETURNS @privilege table(itempos varchar(15), runp bit, selectp bit, insertp bit, 
updatep bit, deletep bit, printp bit, lockp bit, unlockp bit, export bit, setup bit)
AS

  BEGIN
    DECLARE @level int
    DECLARE @group TABLE(parentid varchar(20), parentkey int, group_level int)

    INSERT INTO @group SELECT * FROM fn_parent(@clientid, @clientkey)

    INSERT INTO @privilege
	  SELECT itempos, runp, selectp, insertp, updatep, deletep, printp, lockp, unlockp, export, setup
	  FROM app_privilege WHERE clientid = @clientid AND clientkey = @clientkey

    DECLARE c1 CURSOR FAST_FORWARD FOR SELECT DISTINCT group_level FROM @group ORDER BY group_level 
    OPEN c1
    FETCH NEXT FROM c1 INTO @level
  
    WHILE @@FETCH_STATUS = 0
    BEGIN
		INSERT INTO @privilege
		SELECT itempos, MAX(CAST(runp as int)), MAX(CAST(selectp as int)), MAX(CAST(insertp as int)), 
					    MAX(CAST(updatep as int)), MAX(CAST(deletep as int)), MAX(CAST(printp as int)), 
					    MAX(CAST(lockp as int)), MAX(CAST(unlockp as int)), MAX(CAST(export as int)), 
					    MAX(CAST(setup as int))
		FROM app_privilege
		WHERE clientkey IN (SELECT parentkey FROM @group WHERE group_level = @level)			
			AND itempos NOT IN (SELECT itempos FROM @privilege)
		GROUP BY itempos

		FETCH NEXT FROM c1 INTO @level
    END
    CLOSE c1
    DEALLOCATE c1

    RETURN
  END
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'fn_privilege', 'all'
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\sp\sp_app_grant.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   DROP PROC sp_app_grant;
GO
/*---------------------------------
 適用：SQL2000/SQL2005/SQL2008
 版本：1.0.0

 日期：2011-08-30	(1.0.1)		peterju
 內容：	app_user 拿掉 sysid_ 欄位

 日期：2011-05-30	(1.0.0)		peterju
 內容：	1.整理出經確認相容於 SQL2005/2008 的語法
		2.權限模組需求尚未確認前，先直接 GRANT TO PUBLIC

---------------------------------*/
--設定存取權限
CREATE PROC sp_app_grant
	@objname	VARCHAR(30),
	@grantstr	VARCHAR(50),
	@revoke		BIT=0		--1=取消授權, 0=授權
AS
  DECLARE @sysid VARCHAR(10), @sql VARCHAR(1000), @dbver VARCHAR(10), @setstr VARCHAR(10);
  DECLARE @xtype VARCHAR(10), @admrole VARCHAR(20), @userrole VARCHAR(20);
  SELECT @setstr=CASE @revoke WHEN 0 THEN 'GRANT' ELSE 'REVOKE' END;
  --SELECT @sysid=ISNULL((SELECT DISTINCT sysid_ FROM app_user),'');
  SELECT @admrole=@sysid+'adm';		--系統管理員角色=@sysid+'adm'
  SELECT @userrole=@sysid+'user';	--一般使用者角色=@sysid+'user'

--資料庫伺服器版本：SQL2000 或 SQL2005, SQL2008
  SELECT @dbver='SQL'+REPLACE(REPLACE(LEFT(@@VERSION,26),'Microsoft SQL Server',''),' ','');

--判斷 @grantstr 是否為 ALL
  IF @dbver IN ('SQL2005','SQL2008') AND @grantstr='ALL'
  BEGIN
    SELECT @xtype=xtype FROM sysobjects WHERE name=@objname;
  /*------------------------------------------------------------
    P ->EXEC
    U ->SELECT, INSERT, DELETE, UPDATE, REFERENCES
    V ->SELECT
    FN->EXEC
    IF->SELECT
    TF->SELECT
  ------------------------------------------------------------*/
    IF @xtype='U'			--Table
      SELECT @grantstr='SELECT, INSERT, DELETE, UPDATE'
    ELSE IF @xtype='V'			--View
      SELECT @grantstr='SELECT'
    ELSE IF @xtype IN ('P','FN')	--Stored procedure, User-defined function
      SELECT @grantstr='EXEC'
    ELSE IF @xtype IN ('IF','TF')	--IF function, TF function
      SELECT @grantstr='SELECT';
  END;

  IF @sysid<>''
  BEGIN
	/*
	--begin 1.0.0
    IF @objname IN ('sp_applogin','sp_app_addaudit')
    BEGIN
      SELECT @sql=@setstr+' '+@grantstr+' ON '+@objname+' TO '+@sysid+'login'
      EXEC (@sql);
    END
    ELSE
    BEGIN
      SELECT @sql=@setstr+' '+@grantstr+' ON '+@objname+' TO '+@admrole;
      EXEC (@sql);

      SELECT @sql=@setstr+' '+@grantstr+' ON '+@objname+' TO '+@userrole;
      EXEC (@sql);
    END;
	*/
	SELECT @sql=@setstr+' '+@grantstr+' ON '+@objname+' TO public';
	
	--end 1.0.0
  END;

  RETURN 0;

GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_app_grant','EXEC';
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\sp\sp_backup_data.sql"  
IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_backup_data') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   DROP PROC sp_backup_data;
GO
/*---------------------------------
版本：1.0.4
日期：2017-09-02
內容：加入 BINARY, VARBINARY 與 DATE 支援

版本：1.0.3
日期：2014-10-17
內容：修正有自動增號欄位的判斷

版本：1.0.2 用xusertype取代xtype
---------------------------------*/
--轉移來源資料表內容至目的資料表名稱
CREATE PROC [dbo].[sp_backup_data]
	@sname	VARCHAR(50),	--來源資料表名稱
	@dname	VARCHAR(50)	--目的資料表名稱
AS
  DECLARE @t1 TABLE (order_ TINYINT, colname_ VARCHAR(50), pname_ VARCHAR(20));
  DECLARE @t2 TABLE (order_ TINYINT, colname_ VARCHAR(50), pname_ VARCHAR(20));
  
  --begin 1.0.0
  INSERT INTO @t1
    SELECT c.colid AS order_, c.name AS colname_, p.name AS pname_
      FROM sysobjects t
      INNER JOIN syscolumns c ON t.id=c.id
      INNER JOIN systypes p ON c.xusertype=p.xusertype
      WHERE t.name=@dname;

  INSERT INTO @t2
    SELECT c.colid AS order_, c.name AS colname_, p.name AS pname_
      FROM sysobjects t
      INNER JOIN syscolumns c ON t.id=c.id
      INNER JOIN systypes p ON c.xusertype=p.xusertype
     WHERE t.name=@sname;
  --end 1.0.0

  DECLARE @order TINYINT, @pname VARCHAR(20), @col1 VARCHAR(50), @col2 VARCHAR(50),
          @str1 VARCHAR(8000), @str2 VARCHAR(8000), @ids1 VARCHAR(255), @ids2 VARCHAR(255);

--有自動增號欄位的情況(SET IDENTITY_INSERT tablename ON)--
  IF EXISTS (SELECT 1 FROM sysobjects t
             INNER JOIN syscolumns c ON t.id=c.id
             INNER JOIN systypes p ON c.xtype=p.xtype
              WHERE t.name=@dname AND c.status = 128)
    SELECT @ids1='SET IDENTITY_INSERT '+@dname+' ON '+CHAR(13)+CHAR(10),
           @ids2=CHAR(13)+CHAR(10)+'SET IDENTITY_INSERT '+@dname+' OFF '+CHAR(13)+CHAR(10)
--無自動增號欄位的情況(免設定)--
  ELSE
    SELECT @ids1='', @ids2='';

  SELECT @str1='INSERT INTO '+@dname+' (',  @str2='  SELECT ';

--組合 SQL Script--1.0.0
  DECLARE #c1 CURSOR LOCAL FAST_FORWARD FOR
    SELECT distinct t1.order_, t1.pname_, '['+t1.colname_+']' AS col1_, '['+t2.colname_+']' AS col2_
      FROM @t1 t1
      LEFT JOIN @t2 t2
     ON t1.colname_=t2.colname_
     ORDER BY t1.order_;
  OPEN #c1;
  FETCH NEXT FROM #c1 INTO @order, @pname, @col1, @col2;
  WHILE @@FETCH_STATUS=0
  BEGIN
    SELECT @str1=@str1+@col1;

    IF @col1=@col2
    BEGIN
    --當欄位已存在且值為NULL時, 使用ISNULL填上預設值
      IF UPPER(@pname) IN ('BIGINT','BIT','DECIMAL','FLOAT','INT','MONEY','NUMERIC','REAL','SMALLINT','SMALLMONEY','TIMESTAMP','TINYINT')
        SELECT @str2=@str2+'ISNULL('+@col2+',0)'
      ELSE IF UPPER(@pname) IN ('CHAR','TEXT','VARCHAR', 'DATE')
        SELECT @str2=@str2+'ISNULL('+@col2+','''')'
      ELSE IF UPPER(@pname) IN ('NCHAR','NTEXT','NVARCHAR')
        SELECT @str2=@str2+'ISNULL('+@col2+',N'''')'
      ELSE IF UPPER(@pname) IN ('DATETIME','SMALLDATETIME')
        SELECT @str2=@str2+'ISNULL('+@col2+',0)' --1.0.1
      ELSE IF UPPER(@pname) IN ('BINARY', 'VARBINARY')
        SELECT @str2=@str2+'ISNULL('+@col2+',(0X))'
      ELSE
        SELECT @str2=@str2+@col2;
    END
    ELSE
    BEGIN
      IF UPPER(@pname) IN ('BIGINT','BIT','DECIMAL','FLOAT','INT','MONEY','NUMERIC','REAL','SMALLINT','SMALLMONEY','TIMESTAMP','TINYINT')
        SELECT @str2=@str2+'0'
      ELSE IF UPPER(@pname) IN ('CHAR','TEXT','VARCHAR', 'DATE')
        SELECT @str2=@str2+''''''
      ELSE IF UPPER(@pname) IN ('NCHAR','NTEXT','NVARCHAR', 'VARBINARY')
        SELECT @str2=@str2+'N'''''
      ELSE IF UPPER(@pname) IN ('DATETIME','SMALLDATETIME')
        SELECT @str2=@str2+'0'	--1.0.1
      ELSE IF UPPER(@pname) IN ('BINARY', 'VARBINARY')
        SELECT @str2=@str2+'(0X)'
      ELSE
        SELECT @str2=@str2+'NULL';
    END;

    FETCH NEXT FROM #c1 INTO @order, @pname, @col1, @col2;

    IF @@FETCH_STATUS=0
      SELECT @str1=@str1+', ', @str2=@str2+', ';
  END;
  CLOSE #c1;
  DEALLOCATE #c1;
  SELECT @str1=@ids1+@str1+')'+CHAR(13)+CHAR(10), 
         @str2=@str2+' FROM '+@sname+' WITH (HOLDLOCK TABLOCK)'+@ids2;

  --除錯用訊息，有需要才打開
  --PRINT @str1+@str2
  EXEC (@str1+@str2);

  RETURN 0;


GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\sp\sp_find.sql"  
if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[sp_find]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)
drop procedure [dbo].[sp_find]
GO

/*---------------------------------
 版本：1.0.1

 日期：2013-08-15
 內容：可搜尋 SP,function,trigger,view內含特定字串
       for IT
---------------------------------*/

CREATE	 PROC [dbo].[sp_find]
   @SEARCHSTRING VARCHAR(255), @notcontain Varchar(255)
AS	

--DECLARE @SEARCHSTRING VARCHAR(255), @notcontain Varchar(255)

--SELECT @SEARCHSTRING = 'fn_check_proj_law', @notcontain = ''

SELECT DISTINCT sysobjects.name AS [Object Name] ,
case when sysobjects.xtype = 'P' then 'Stored Proc'
when sysobjects.xtype = 'TF' then 'Function'
when sysobjects.xtype = 'TR' then 'Trigger'
when sysobjects.xtype = 'V' then 'VIEW'
end as [Object Type],syscomments.text
FROM sysobjects,syscomments
WHERE sysobjects.id = syscomments.id
AND sysobjects.type in ('P','TF','TR','V')
AND sysobjects.category = 0
AND CHARINDEX(@SEARCHSTRING,syscomments.text)>0
AND ((CHARINDEX(@notcontain,syscomments.text)=0 
or CHARINDEX(@notcontain,syscomments.text)<>0))

--MSSQL2008R2 object types:
--AF = 彙總函式 (CLR)
--C = CHECK 條件約束
--D = 預設值或 DEFAULT 條件約束
--F = FOREIGN KEY 條件約束
--L = 記錄
--FN = 純量函數
--FS = 組件 (CLR) 純量函數
--FT = 組件 (CLR) 資料表值函式
--IF = 內嵌資料表函數
--IT = 內部資料表
--P = 預存程序
--PC = 組件 (CLR) 預存程序
--PK = PRIMARY KEY 條件約束 (類型是 K)
--RF = 複寫篩選預存程序
--S = 系統資料表
--SN = 同義字
--SQ = 服務佇列
--TA = 組件 (CLR) DML 觸發程序
--TF = 資料表函數
--TR = SQL DML 觸發程序
--TT = 資料表類型
--U = 使用者資料表
--UQ = UNIQUE 條件約束 (類型是 K)
--V = 檢視
--X = 擴充預存程序
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\sp\sp_setup.sql"  
if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[sp_setup]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)
drop procedure [dbo].[sp_setup]
GO

/*---------------------------------
 版本：1.0.1

 日期：2012-01-12	
 內容：新增@local參數-0.本機 1.LDAP

 日期：2011-12-05	
 內容：設定 app_winuser 的管理者帳號
---------------------------------*/
CREATE PROC sp_setup
   @winuser varchar(20),
   @local bit
AS

set nocount on;

begin tran

delete from app_winuser where userid='admin' and winuser=@winuser;
if @local=0
	insert into app_winuser
	select 'admin', @winuser, 'ADASIAPAC', 'admin', '', 1, @winuser, GETDATE(), @winuser, GETDATE()
else
	insert into app_winuser
	select 'admin', @winuser, HOST_NAME(), 'admin', '', 1, @winuser, GETDATE(), @winuser, GETDATE()

commit tran

PRINT '已將'+@winuser+'設定為管理者'


GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'sp_setup','EXEC';
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\0.app_table_all.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/3/21
 內容 : app_table(資料表頭檔)
 內容 : app_table_field(資料字典檔)
 內容 : app_table_field_option(選項檔)
 內容 : app_table_field_option_item(選項項目檔)
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--app_table begin-----------------------------------------------------------------------
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_table] (
	[tablename]		VARCHAR(40) NOT NULL,
	[chinesename]		VARCHAR(40) NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_table]') AND type in (N'U'))
	EXEC sp_backup_data 'app_table', 'Tmp_app_table'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_table]') AND type in (N'U'))
	DROP TABLE app_table;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_table', 'app_table', 'OBJECT'
GO

ALTER TABLE [dbo].[app_table] ADD 
	CONSTRAINT [PK_app_table] PRIMARY KEY  CLUSTERED 
	(
	  [tablename]
	)  ON [PRIMARY] 
GO
--app_table_field begin-----------------------------------------------------------------------
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_table_field] (
	[tablename]		VARCHAR(40) NOT NULL,
	[fieldname]		VARCHAR(40) NOT NULL,
	[field_idx]		INT NULL,
	[ctitle]		VARCHAR(40) NULL,
	[etitle]		VARCHAR(40) NULL,
	[ins_only]		BIT NULL,
	[not_null]		BIT NULL,
	[readonly]		BIT NULL,
	[edt_mask]		VARCHAR(50) NULL,
	[dgt_type]		SMALLINT NULL,
	[opt_type]		SMALLINT NULL,
	[cap_type]		SMALLINT NULL,
	[default_value]		VARCHAR(50) NULL,
	[grid_visible]		BIT NULL,
	[grid_idx]		INT NULL,
	[grid_width]		INT NULL,
	[edt_type]		VARCHAR(20) NULL,
	[loguser]		VARCHAR(20) NULL,
	[logtime]		DATETIME NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_table_field]') AND type in (N'U'))
	EXEC sp_backup_data 'app_table_field', 'Tmp_app_table_field'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_table_field]') AND type in (N'U'))
	DROP TABLE app_table_field;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_table_field', 'app_table_field', 'OBJECT'
GO

ALTER TABLE [dbo].[app_table_field] ADD 
	CONSTRAINT [PK_app_table_field] PRIMARY KEY  CLUSTERED 
	(
	  [tablename],
	  [fieldname]
	)  ON [PRIMARY] 
GO
--app_table_field_option begin-----------------------------------------------------------------------
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_table_field_option] (
	[opt_no]		SMALLINT NOT NULL,
	[name]		  VARCHAR(100) NULL,
	[readonly]		BIT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_table_field_option]') AND type in (N'U'))
	EXEC sp_backup_data 'app_table_field_option', 'Tmp_app_table_field_option'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_table_field_option]') AND type in (N'U'))
	DROP TABLE app_table_field_option;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_table_field_option', 'app_table_field_option', 'OBJECT'
GO

ALTER TABLE [dbo].[app_table_field_option] ADD 
	CONSTRAINT [PK_app_table_field_option] PRIMARY KEY  CLUSTERED 
	(
	  [opt_no]
	)  ON [PRIMARY] 
GO
--app_table_field_option_item begin-----------------------------------------------------------------------
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_table_field_option_item] (
	[opt_no]		SMALLINT NOT NULL,
	[item_no]		SMALLINT NOT NULL,
	[name]		VARCHAR(200) NULL,
	[loguser]		VARCHAR(20) NULL,
	[logtime]		DATETIME NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_table_field_option_item]') AND type in (N'U'))
	EXEC sp_backup_data 'app_table_field_option_item', 'Tmp_app_table_field_option_item'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_table_field_option_item]') AND type in (N'U'))
	DROP TABLE app_table_field_option_item;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_table_field_option_item', 'app_table_field_option_item', 'OBJECT'
GO

ALTER TABLE [dbo].[app_table_field_option_item] ADD 
	CONSTRAINT [PK_app_table_field_option_item] PRIMARY KEY  CLUSTERED 
	(
	  [opt_no],
	  [item_no]
	)  ON [PRIMARY] 
GO
--app_table_field_option_item begin-----------------------------------------------------------------------
--6.完成(買單).....
COMMIT;

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_table', 'ALL';

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_table_field', 'ALL';

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_table_field_option', 'ALL';

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_table_field_option_item', 'ALL';

--app_table begin-----------------------------------------------------------------------

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_table', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '資料表頭檔'; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'tablename', 1, '資料表名稱', 'tablename', 0, 0, 0, '', 0, 0, 0, '', 0, 1, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'chinesename', 2, '欄位名稱', 'chinesename', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 100, 'TextEdit', @loguser, @dt;
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_table';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no=a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE popt_no=a.popt_no AND opt_no=a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 

--app_table_field begin-----------------------------------------------------------------------

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_table_field', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '資料字典檔'; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'tablename', 1, '資料表名稱', 'tablename', 0, 0, 0, '', 0, 0, 0, '', 0, 1, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fieldname', 2, '欄位名稱', 'fieldname', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'field_idx', 3, '欄位順序', 'field_idx', 0, 0, 0, '', 0, 0, 0, '0', 1, 2, 80, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ctitle', 4, '中文名稱', 'ctitle', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'etitle', 5, '英文名稱', 'etitle', 0, 0, 0, '', 0, 0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ins_only', 6, '新增後不可修改', 'ins_only', 0, 0, 0, '', 0, 0, 0, 'False', 1, 6, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'not_null', 7, '不可空值', 'not_null', 0, 0, 0, '', 0, 0, 0, 'False', 1, 7, 200, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'readonly', 8, '唯讀', 'readonly', 0, 0, 0, '', 0, 0, 0, 'False', 1, 8, 50, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'edt_mask', 9, 'edt_mask', 'edt_mask', 0, 0, 0, '', 0, 0, 0, '', 1, 8, 50, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'dgt_type', 10, '數值類別', 'dgt_type', 0, 0, 0, '', 0, 901, 0, '0', 1, 10, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'opt_type', 11, '選項類別', 'opt_type', 0, 0, 0, '', 0, 0, 0, '0', 1, 11, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cap_type', 12, '大小寫', 'cap_type', 0, 0, 0, '', 0, 902, 0, '', 1, 8, 50, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'default_value', 13, '預設值', 'default_value', 0, 0, 0, '', 0, 0, 0, '', 0, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'grid_visible', 14, '表格顯示', 'grid_visible', 0, 0, 0, '', 0, 0, 0, 'False', 1, 13, 80, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'grid_idx', 15, '表格順序', 'grid_idx', 0, 0, 0, '', 0, 0, 0, '0', 1, 14, 80, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'grid_width', 16, '表格寬度', 'grid_width', 0, 0, 0, '', 0, 0, 0, '0', 1, 15, 80, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'edt_type', 17, '控制項類別', 'edt_type', 0, 0, 0, '', 0, 0, 0, '', 0, 16, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser', 18, '異動人員', '異動人員', 0, 0, 0, '', 0, 0, 0, '', 1, 18, 50, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime', 19, '異動時間', '異動時間', 0, 0, 0, '', 0, 0, 0, '', 1, 17, 150, 'DateEdit', @loguser, @dt;
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_table_field';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 

IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no=a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE popt_no=a.popt_no AND opt_no=a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 

--app_table_field_option begin-----------------------------------------------------------------------

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_table_field_option', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '選項檔'; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'opt_no', 1, '編號', 'opt_no', 0, 0, 0, '', 0, 0, 0, '', 0, 1, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name', 2, '名稱', 'name', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'readonly', 3, '唯讀', 'readonly', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 100, 'TextEdit', @loguser, @dt;
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_table_field_option';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no=a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE popt_no=a.popt_no AND opt_no=a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 

--app_table_field_option_item begin----------------------------------------------------------------------- 

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_table_field_option_item', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '選項項目檔'; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'opt_no', 1, '選項編號', 'opt_no', 0, 0, 0, '', 0, 0, 0, '', 0, 1, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'item_no', 2, '項目編號', 'item_no', 0, 0, 0, '', 0, 0, 0, '', 0, 1, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name', 3, '名稱', 'name', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 100, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser', 4, '異動人員', '異動人員', 0, 0, 0, '', 0, 0, 0, '', 1, 18, 50, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime', 5, '異動時間', '異動時間', 0, 0, 0, '', 0, 0, 0, '', 1, 17, 150, 'DateEdit', @loguser, @dt;
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_table_field_option_item';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no=a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE popt_no=a.popt_no AND opt_no=a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 

--app_table_field_option_item begin----------------------------------------------------------------------- 

PRINT '更新 app_table, app_table_field, app_table_field_option, app_table_field_option_item 結束!' 
GO 

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_datachange.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 吳欣融
 日期 : 2014-05-13
 內容 : app_datachange
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_datachange] (
	[change_no]  	VARCHAR(12) NOT NULL,
	[change_user]	VARCHAR(20) NOT NULL,
	[change_time]	DATETIME NOT NULL,
	[note]       	NVARCHAR(300) NOT NULL,
	[command]    	VARCHAR(MAX) NOT NULL,
	[isAdjusted] 	BIT NOT NULL,
	[loguser]    	VARCHAR(20) NOT NULL,
	[logtime]    	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_datachange]') AND type in (N'U'))
	EXEC sp_backup_data 'app_datachange', 'Tmp_app_datachange'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_datachange]') AND type in (N'U'))
	DROP TABLE app_datachange;

EXEC sp_rename 'Tmp_app_datachange', 'app_datachange', 'OBJECT'
GO

ALTER TABLE [dbo].[app_datachange] ADD CONSTRAINT [PK_app_datachange] PRIMARY KEY CLUSTERED
(
	[change_no]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_datachange', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_datachange', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '異動記錄主檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'change_no'  ,  1, '異動單號', '異動單號', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'change_user',  2, '異動人員', '異動人員', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'change_time',  3, '異動時間', '異動時間', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'       ,  4, '註解'    , '註解'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'command'    ,  5, '異動語法', '異動語法', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'isAdjusted' ,  6, '異動完成', '異動完成', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'    ,  7, '放行人員', '放行人員', 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'    ,  8, '放行時間', '放行時間', 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_datachange';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_datachange Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_datachangelist.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 吳欣融
 日期 : 2014-12-11
 內容 : app_datachangelist
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_datachangelist] (
	[change_no]   	VARCHAR(12) NOT NULL,
	[tablename]   	VARCHAR(40) NOT NULL,
	[fieldname]   	VARCHAR(40) NOT NULL,
	[fieldCname]  	VARCHAR(40) NOT NULL,
	[idFieldValue]	NVARCHAR(100) NOT NULL,
	[oldValue]    	NVARCHAR(500) NOT NULL,
	[newValue]    	NVARCHAR(500) NOT NULL,
	[keyValue]    	NVARCHAR(500) NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_datachangelist]') AND type in (N'U'))
	EXEC sp_backup_data 'app_datachangelist', 'Tmp_app_datachangelist'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_datachangelist]') AND type in (N'U'))
	DROP TABLE app_datachangelist;	
	
EXEC sp_rename 'Tmp_app_datachangelist', 'app_datachangelist', 'OBJECT'
GO	

ALTER TABLE [dbo].[app_datachangelist] ADD CONSTRAINT [PK_app_datachangelist] PRIMARY KEY CLUSTERED
(
	[change_no],[tablename],[fieldname],[idFieldValue]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_datachangelist', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_datachangelist', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '異動記錄明細檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'change_no'   ,  1, '異動單號'        , '異動單號'        , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tablename'   ,  2, '異動資料表名稱'  , '異動資料表名稱'  , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fieldname'   ,  3, '異動欄位名稱'    , '異動欄位名稱'    , 1, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fieldCname'  ,  4, '異動欄位中文名稱', '異動欄位中文名稱', 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'idFieldValue',  5, '異動辨識欄位內容', '異動辨識欄位內容', 1, 1, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'oldValue'    ,  6, '異動前資料'      , '異動前資料'      , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'newValue'    ,  7, '異動後資料'      , '異動後資料'      , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'keyValue'    ,  8, '異動欄位主鍵內容', '異動欄位主鍵內容', 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  9, '修改人員'        , '修改人員'        , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     , 10, '修改時間'        , '修改時間'        , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_datachangelist';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_datachangelist Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_data_stream.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000250
 日期 : 2014-07-17
 內容 : app_data_stream
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_data_stream] (
	[change_no] 	VARCHAR(12) NOT NULL,
	[tablename] 	VARCHAR(40) NOT NULL,
	[key]       	INT NOT NULL,
	[isAdjusted]	BIT NOT NULL,
	[byte]      	NVARCHAR(MAX) NOT NULL,
	[loguser]   	VARCHAR(20) NOT NULL,
	[logtime]   	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_data_stream]') AND type in (N'U'))
	EXEC sp_backup_data 'app_data_stream', 'Tmp_app_data_stream'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_data_stream]') AND type in (N'U'))
	DROP TABLE app_data_stream;

EXEC sp_rename 'Tmp_app_data_stream', 'app_data_stream', 'OBJECT'
GO

ALTER TABLE [dbo].[app_data_stream] ADD CONSTRAINT [PK_app_data_stream] PRIMARY KEY CLUSTERED
(
	[change_no],[tablename],[key]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_data_stream', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_data_stream', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '資料流異動檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'change_no' ,  1, '異動單號'      , '異動單號'      , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tablename' ,  2, '異動資料表名稱', '異動資料表名稱', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'key'       ,  3, '資料表鍵值'    , '資料表鍵值'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'isAdjusted',  4, '異動完成'      , '異動完成'      , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'byte'      ,  5, 'byte'          , 'byte'          , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'   ,  6, '異動人員'      , '異動人員'      , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'   ,  7, '異動時間'      , '異動時間'      , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_data_stream';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_data_stream Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_menu.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/4/23
 內容 : app_menu()
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_menu] (
	[sno]		INT NOT NULL,
	[itempos]		VARCHAR(15) NOT NULL,
	[pkgname]		VARCHAR(30) NOT NULL,
	[itemid]		INT NOT NULL,
	[itemcaption]		VARCHAR(50) NOT NULL,
	[itemhint]		VARCHAR(50) NOT NULL,
	[typename]		VARCHAR(50) NOT NULL,
	[begingroup]		BIT NOT NULL,
	[pkgaversion]		VARCHAR(20) NOT NULL,
	[runp]		BIT NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_menu]') AND type in (N'U'))
	EXEC sp_backup_data 'app_menu', 'Tmp_app_menu'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_menu]') AND type in (N'U'))
	DROP TABLE app_menu;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_menu', 'app_menu', 'OBJECT'
GO

ALTER TABLE [dbo].[app_menu] ADD 
	CONSTRAINT [PK_app_menu] PRIMARY KEY  CLUSTERED 
	(
	  [itempos]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_menu', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_menu', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '交易選單檔'; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_menu';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_menu 結束!' 
GO 
SET ANSI_PADDING OFF
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_message.sql"  
--this script is created by SpecCreator
/*---------------------------------
 版本 : 1
 日期 : 2014-04-09
 內容 : app_message
---------------------------------*/
BEGIN TRANSACTION 

--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_message] (
	[seq]         	VARCHAR(14) NOT NULL,
	[start_date]  	DATETIME NOT NULL,
	[due_date]    	DATETIME NOT NULL,
	[msg_text]    	VARCHAR(200) NOT NULL,
	[pno]         	INT NOT NULL,
	[userid]      	VARCHAR(20) NOT NULL,
	[is_important]	BIT NOT NULL,
	[is_end]      	BIT NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL	
);
  
--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_message]') AND type in (N'U'))
	EXEC sp_backup_data 'app_message', 'Tmp_app_message'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_message]') AND type in (N'U'))
	DROP TABLE app_message;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_message', 'app_message', 'OBJECT'
GO

ALTER TABLE [dbo].[app_message] ADD CONSTRAINT [PK_app_message] PRIMARY KEY CLUSTERED
(
	[seq]
)   
ON [PRIMARY]
GO

--6.完成(買單).....
COMMIT;

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_message', 'ALL';

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_message', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '系統訊息檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'seq'         ,  1, '序號'    , '序號'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'start_date'  ,  2, '開始日期', '開始日期', 0, 0, 0, '', 0,   0, 0, '', 1, 2, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'due_date'    ,  3, '結束日期', '結束日期', 0, 0, 0, '', 0,   0, 0, '', 1, 3, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'msg_text'    ,  4, '訊息內容', '訊息內容', 0, 0, 0, '', 0,   0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'pno'         ,  5, '客戶帳號', '客戶帳號', 0, 0, 0, '', 0,   0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'userid'      ,  6, '使用者ID', '使用者ID', 0, 0, 0, '', 0,   0, 0, '', 1, 6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_important',  7, '重要訊息', '重要訊息', 0, 0, 0, '', 0,   0, 0, '', 1, 7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_end'      ,  8, '結束'    , '結束'    , 0, 0, 0, '', 0,   0, 0, '', 1, 8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  9, '異動人員', '異動人員', 0, 0, 0, '', 0,   0, 0, '', 0, 99, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     , 10, '異動時間', '異動時間', 0, 0, 0, '', 0,   0, 0, '', 0, 99, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1 
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--將欄位次序調整成與 Table Scheme 相同
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_message';

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT '更新 app_message 結束!'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_option.sql"  
 /*---------------------------------
 版本 : 1.0.0
 日期 : 2012/10/26
 內容 : app_option()
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_option] (
	[opt_name]		VARCHAR(30) NOT NULL,
	[opt_value]		NVARCHAR(150) NOT NULL,
	[opt_note]		VARCHAR(200) NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_option]') AND type in (N'U'))
	EXEC sp_backup_data 'app_option', 'Tmp_app_option'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_option]') AND type in (N'U'))
	DROP TABLE app_option;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_option', 'app_option', 'OBJECT'
GO

ALTER TABLE [dbo].[app_option] ADD 
	CONSTRAINT [PK_app_option] PRIMARY KEY  CLUSTERED 
	(
	  [opt_name]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_option', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_option', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_option';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_option 結束!' 
GO 
SET ANSI_PADDING OFF
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_permission.sql"  
/*---------------------------------
版本 : 1.0.0
日期 : 2014/7/22
內容 : New Version
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION

CREATE TABLE [dbo].[Tmp_app_permission] (
	[itempos]		VARCHAR(15) NOT NULL,
	[userid]		VARCHAR(50) NOT NULL,
	[pno]		INT NOT NULL,
	[selectp]		BIT NOT NULL,
	[insertp]		BIT NOT NULL,
	[updatep]		BIT NOT NULL,
	[deletep]		BIT NOT NULL,
	[printp]		BIT NOT NULL,
	[lockp]		BIT NOT NULL,
	[unlockp]		BIT NOT NULL,
	[export]		BIT NOT NULL,
	[loguser]		VARCHAR(20) NOT NULL,
	[logtime]		DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_permission]') AND type in (N'U'))
	EXEC sp_backup_data 'app_permission', 'Tmp_app_permission'

IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_permission]') AND type in (N'U'))
	DROP TABLE app_permission;

EXEC sp_rename 'Tmp_app_permission', 'app_permission', 'OBJECT'
GO

ALTER TABLE [dbo].[app_permission] ADD 
	CONSTRAINT [PK_app_permission] PRIMARY KEY  CLUSTERED 
	(
	  [itempos],
	  [userid],
	  [pno]
	)  ON [PRIMARY] 
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure') = 1)
EXEC sp_app_grant 'app_permission', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_permission', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
IF @owfield = 1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 

  UPDATE a SET a.field_idx = c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_permission';  

  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption = 1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE pno = a.pno AND opt_no = a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_permission 結束!' 
GO 
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_privilege.sql"  
/*---------------------------------
版本 : 1.0.0
日期 : 2014/7/22
內容 : New Version
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_privilege] (
	[itempos]		VARCHAR(15) NOT NULL,
	[clientid]		VARCHAR(20) NOT NULL,
	[clientkey]     INT NOT NULL,
	[runp]			BIT NOT NULL,
	[selectp]		BIT NOT NULL,
	[insertp]		BIT NOT NULL,
	[updatep]		BIT NOT NULL,
	[deletep]		BIT NOT NULL,
	[printp]		BIT NOT NULL,
	[lockp]			BIT NOT NULL,
	[unlockp]		BIT NOT NULL,
	[export]		BIT NOT NULL,
	[setup]			BIT NOT NULL,
	[loguser]		VARCHAR(20) NOT NULL,
	[logtime]		DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_privilege]') AND type in (N'U'))
	EXEC sp_backup_data 'app_privilege', 'Tmp_app_privilege'

IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_privilege]') AND type in (N'U'))
	DROP TABLE app_privilege;

EXEC sp_rename 'Tmp_app_privilege', 'app_privilege', 'OBJECT'
GO

ALTER TABLE [dbo].[app_privilege] ADD 
	CONSTRAINT [PK_app_privilege] PRIMARY KEY  CLUSTERED 
	(
	  [itempos],
	  [clientid],
	  [clientkey]
	)  ON [PRIMARY] 
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure') = 1)
EXEC sp_app_grant 'app_privilege', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_privilege', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
IF @owfield = 1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 

  UPDATE a SET a.field_idx = c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_privilege';  

  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption = 1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND opt_no = a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_privilege 結束!' 
GO 
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_privilege_log.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2014-09-22
 內容 : app_privilege_log
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_privilege_log] (
    [changedno]    VARCHAR(10) NOT NULL,
    [clientkey]    INT NOT NULL,
    [clientid]     VARCHAR(20) NOT NULL,
    [itempos]      VARCHAR(15) NOT NULL,
    [itemcaption]  VARCHAR(50) NOT NULL,
    [byGroup]      BIT NOT NULL,
    [runp]         BIT NOT NULL,
    [selectp]      BIT NOT NULL,
    [insertp]      BIT NOT NULL,
    [updatep]      BIT NOT NULL,
    [deletep]      BIT NOT NULL,
    [printp]       BIT NOT NULL,
    [lockp]        BIT NOT NULL,
    [unlockp]      BIT NOT NULL,
    [export]       BIT NOT NULL,
    [setup]        BIT NOT NULL,
    [loguser]      VARCHAR(20) NOT NULL,
    [logtime]      DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_privilege_log]') AND type in (N'U'))
    EXEC sp_backup_data 'app_privilege_log', 'Tmp_app_privilege_log'
    
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_privilege_log]') AND type in (N'U'))
    DROP TABLE app_privilege_log;    
    
EXEC sp_rename 'Tmp_app_privilege_log', 'app_privilege_log', 'OBJECT'
GO    

ALTER TABLE [dbo].[app_privilege_log] ADD CONSTRAINT [PK_app_privilege_log] PRIMARY KEY CLUSTERED
(
    [changedno],[clientkey],[clientid],[itempos]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'app_privilege_log', 'ALL';
    
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_privilege_log', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'privilege change log';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'changedno',  1, 'Seq'    , 'Seq'    , 1, 1, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'clientkey',  2, 'clientkey'   , 'clientkey'   , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'clientid' ,  3, 'clientid'    , 'clientid'    , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'itempos'  ,  4, 'Menu Item'    , 'Menu Item'    , 1, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'itemcaption', 1, 'Caption'    , 'Caption'    , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'byGroup'  ,  5, 'Changed By Group', 'Changed By Group', 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'runp'     ,  6, 'Executive'        , 'Executive'        , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'selectp'  ,  7, 'Query'        , 'Query'        , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'insertp'  ,  8, 'Insert'        , 'Insert'        , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'updatep'  ,  9, 'Modify'        , 'Modify'        , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'deletep'  , 10, 'Delete'        , 'Delete'        , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'printp'   , 11, 'Print'        , 'Print'        , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lockp'    , 12, 'Lock'        , 'Lock'        , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'unlockp'  , 13, 'Unlock'        , 'Unlock'        , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'export'   , 14, 'Export'        , 'Export'        , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'setup'    , 15, 'Setup'        , 'Setup'        , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'  , 16, 'Log User'    , 'Log User'    , 0, 0, 0, '', 0,   0, 0, '', 0, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'  , 17, 'Log Time'    , 'Log Time'    , 0, 0, 0, '', 0,   0, 0, '', 0, 17, 150, 'DateEdit', @loguser, @dt;
    

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_privilege_log';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_privilege_log Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_quick_menu.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/12/31
 內容 : app_quick_menu
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_quick_menu] (
	[name]       VARCHAR(20) NOT NULL,
	[itempos]    VARCHAR(15) NOT NULL    
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_quick_menu]') AND type in (N'U'))
	EXEC sp_backup_data 'app_quick_menu', 'Tmp_app_quick_menu'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_quick_menu]') AND type in (N'U'))
	DROP TABLE app_quick_menu;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_quick_menu', 'app_quick_menu', 'OBJECT'
GO

ALTER TABLE [dbo].[app_quick_menu] ADD 
	CONSTRAINT [PK_app_quick_menu] PRIMARY KEY  CLUSTERED 
	(
	  [name]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_quick_menu', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_quick_menu', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '快速查詢選單'; 
	SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
	INSERT #appTableField SELECT @tbname, 'name', 1, '自定義名稱', '自定義名稱', 1, 1, 0, '', 0, 0, 0, '', 1, 1, 150, '', @loguser, @dt;
	INSERT #appTableField SELECT @tbname, 'itempos', 2, '選單', '選單', 1, 1, 0, '', 0, 0, 0, '', 1, 2, 150, '', @loguser, @dt;	

	DELETE app_table_field WHERE tablename = @tbname; 
	INSERT app_table_field SELECT * FROM #appTableField; 
	DROP TABLE #appTableField; 
	
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_quick_menu';  
     
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 


IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
     
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_quick_menu 結束!' 
GO 
SET ANSI_PADDING OFF
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_report.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/4/23
 內容 : app_report()
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_report] (
	[itempos]		VARCHAR(15) NOT NULL,
	[maintitle]		VARCHAR(60) NOT NULL,
	[subtitle]		VARCHAR(60) NOT NULL,
	[rpt_footer]		VARCHAR(100) NOT NULL,
	[page_footer]		VARCHAR(100) NOT NULL,
	[qrcompany]		BIT NOT NULL,
	[qruser]		BIT NOT NULL,
	[qrprogram]		BIT NOT NULL,
	[qrreport]		BIT NOT NULL,
	[qrdate]		BIT NOT NULL,
	[qrtime]		BIT NOT NULL,
	[qrpage]		BIT NOT NULL,
	[reset_pno]		BIT NOT NULL,
	[loguser]		VARCHAR(20) NOT NULL,
	[logtime]		DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_report]') AND type in (N'U'))
	EXEC sp_backup_data 'app_report', 'Tmp_app_report'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_report]') AND type in (N'U'))
	DROP TABLE app_report;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_report', 'app_report', 'OBJECT'
GO

ALTER TABLE [dbo].[app_report] ADD 
	CONSTRAINT [PK_app_report] PRIMARY KEY  CLUSTERED 
	(
	  [itempos]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_report', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_report', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '報表設定檔'; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'itempos', 1, 'Report Number', 'itempos', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'maintitle', 2, 'Main Title', 'maintitle', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'subtitle', 3, 'Subtitle', 'subtitle', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rpt_footer', 4, 'Report Footer', 'rpt_footer', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'page_footer', 5, 'Page Footer', 'page_footer', 0, 0, 0, '', 0, 0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'qrcompany', 6, 'Corp. Name', 'qrcompany', 0, 0, 0, '', 0, 0, 0, 'False', 1, 6, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'qruser', 7, 'Printing Staff', 'qruser', 0, 0, 0, '', 0, 0, 0, 'False', 1, 7, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'qrprogram', 8, 'Program Name', 'qrprogram', 0, 0, 0, '', 0, 0, 0, 'False', 1, 8, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'qrreport', 9, 'Report Name', 'qrreport', 0, 0, 0, '', 0, 0, 0, 'False', 1, 9, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'qrdate', 10, 'Print Date', 'qrdate', 0, 0, 0, '', 0, 0, 0, 'False', 1, 10, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'qrtime', 11, 'Print Time', 'qrtime', 0, 0, 0, '', 0, 0, 0, 'False', 1, 11, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'qrpage', 12, 'Printing Page', 'qrpage', 0, 0, 0, '', 0, 0, 0, 'False', 1, 12, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'reset_pno', 13, 'Contract Group Reset Page', 'reset_pno', 0, 0, 0, '', 0, 0, 0, 'False', 1, 13, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser', 14, 'Loguser', '異動人員', 0, 0, 0, '', 0, 0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime', 15, 'Logtime', '異動時間', 0, 0, 0, '', 0, 0, 0, '', 1, 15, 150, 'DateEdit', @loguser, @dt;
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_report';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
  
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_report 結束!' 
GO 
SET ANSI_PADDING OFF
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Report Number' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'itempos'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Main Title' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'maintitle'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Subtitle' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'subtitle'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Report Footer' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'rpt_footer'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Page Footer' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'page_footer'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Corp. Name' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'qrcompany'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Printing Staff' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'qruser'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Program Name' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'qrprogram'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Report Name' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'qrreport'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Print Date' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'qrdate'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Print Time' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'qrtime'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Printing Page' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'qrpage'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Contract Group Reset Page' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'reset_pno'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Loguser' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'loguser'
GO

EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Logtime' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'app_report', @level2type=N'COLUMN',@level2name=N'logtime'
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_role.sql"  
/*---------------------------------
版本 : 1.0.0
日期 : 2014/7/22
內容 : New Version
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION

CREATE TABLE [dbo].[Tmp_app_role] (
    [rolekey]       INT NOT NULL,
    [roleid]        VARCHAR(20) NOT NULL,
    [rolename]      VARCHAR(40) NOT NULL,
    [leaderid]      VARCHAR(20) NOT NULL,
    [is_admin]      BIT NOT NULL,
    [is_reg]        BIT NOT NULL,
    [remark]        VARCHAR(50) NULL,
    [loguser]       VARCHAR(20) NOT NULL,
    [logtime]       DATETIME NOT NULL
);


IF EXISTS (SELECT * FROM sys.objects 
    WHERE object_id = OBJECT_ID(N'[dbo].[app_role]') AND type in (N'U'))
    EXEC sp_backup_data 'app_role', 'Tmp_app_role'


IF EXISTS (SELECT * FROM sys.objects
    WHERE object_id = OBJECT_ID(N'[dbo].[app_role]') AND type in (N'U'))
    DROP TABLE app_role;


EXEC sp_rename 'Tmp_app_role', 'app_role', 'OBJECT'
GO

ALTER TABLE [dbo].[app_role] ADD 
    CONSTRAINT [PK_app_role] PRIMARY KEY  CLUSTERED 
    (
      [rolekey], [roleid]
    )  ON [PRIMARY] 
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure') = 1)
EXEC sp_app_grant 'app_role', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_role', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'rolekey' , 1, '角色主鍵', '角色主鍵', 1, 1, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'roleid'  , 2, '角色代號', '角色代號', 1, 1, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rolename', 3, '角色名稱', '角色名稱', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'leaderid', 4, '主管', '主管', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark'  , 5, '備註說明', '備註說明', 0, 0, 0, '', 0, 0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_admin', 6, 'Is Admin', 'Is Admin', 0, 0, 0, '', 0, 0, 0,  '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_reg'  , 7, 'Is Reg'  , 'Is Reg'  , 0, 0, 0, '', 0, 0, 0,  '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser' , 8, '異動人員', '異動人員', 0, 0, 0, '', 0, 0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime' , 9, '異動時間', '異動時間', 0, 0, 0, '', 0, 0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
IF @owfield = 1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 

  UPDATE a SET a.field_idx = c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_role';  

  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption = 1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND opt_no = a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_role 結束!' 
GO 
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_rpt_export_setting.sql"  
--this script is created by SpecCreator
/*---------------------------------
 版本 : 1
 日期 : 2014-08-13
 內容 : app_rpt_export_setting
---------------------------------*/
BEGIN TRANSACTION 

--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_rpt_export_setting] (
	[rpt]         	VARCHAR(50) NOT NULL,
	[header_left] 	NVARCHAR(200) NOT NULL,
	[header_mid]  	NVARCHAR(200) NOT NULL,
	[header_right]	NVARCHAR(200) NOT NULL,
	[footer_left] 	NVARCHAR(200) NOT NULL,
	[footer_mid]  	NVARCHAR(200) NOT NULL,
	[footer_right]	NVARCHAR(200) NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL	
);
  
--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_rpt_export_setting]') AND type in (N'U'))
	EXEC sp_backup_data 'app_rpt_export_setting', 'Tmp_app_rpt_export_setting'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_rpt_export_setting]') AND type in (N'U'))
	DROP TABLE app_rpt_export_setting;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_rpt_export_setting', 'app_rpt_export_setting', 'OBJECT'
GO

ALTER TABLE [dbo].[app_rpt_export_setting] ADD CONSTRAINT [PK_app_rpt_export_setting] PRIMARY KEY CLUSTERED
(
	[rpt]
)   
ON [PRIMARY]
GO

--6.完成(買單).....
COMMIT;

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_rpt_export_setting', 'ALL';

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_rpt_export_setting', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '報表匯出設定檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'rpt'         ,  1, '報表名稱', '報表名稱', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'header_left' ,  2, '表頭左'  , '表頭左'  , 0, 0, 0, '', 0,   0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'header_mid'  ,  3, '表頭中'  , '表頭中'  , 0, 0, 0, '', 0,   0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'header_right',  4, '表頭右'  , '表頭右'  , 0, 0, 0, '', 0,   0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'footer_left' ,  5, '表尾左'  , '表尾左'  , 0, 0, 0, '', 0,   0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'footer_mid'  ,  6, '表尾中'  , '表尾中'  , 0, 0, 0, '', 0,   0, 0, '', 1, 6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'footer_right',  7, '表尾右'  , '表尾右'  , 0, 0, 0, '', 0,   0, 0, '', 1, 7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  8, '異動人員', '異動人員', 0, 0, 0, '', 0,   0, 0, '', 0, 99, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     ,  9, '異動時間', '異動時間', 0, 0, 0, '', 0,   0, 0, '', 0, 99, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1 
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--將欄位次序調整成與 Table Scheme 相同
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_rpt_export_setting';

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT '更新 app_rpt_export_setting 結束!'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_tracking_button.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Frank
 日期 : 2014-10-17
 內容 : app_tracking_button
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_tracking_button] (
	[clickNo]    	INT IDENTITY(1,1) NOT NULL,
	[userId]     	VARCHAR(20) NOT NULL,
	[clickTime]  	DATETIME NOT NULL,
	[clickForm]  	NVARCHAR(50) NOT NULL,
	[clickButton]	NVARCHAR(100) NOT NULL,
	[IP]         	VARCHAR(40) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_tracking_button]') AND type in (N'U'))
	EXEC sp_backup_data 'app_tracking_button', 'Tmp_app_tracking_button'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_tracking_button]') AND type in (N'U'))
	DROP TABLE app_tracking_button;	
	
EXEC sp_rename 'Tmp_app_tracking_button', 'app_tracking_button', 'OBJECT'
GO	

ALTER TABLE [dbo].[app_tracking_button] ADD CONSTRAINT [PK_app_tracking_button] PRIMARY KEY CLUSTERED
(
	[clickNo]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_tracking_button', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_tracking_button', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '按鈕點擊歷史軌跡';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'clickNo'    ,  1, 'Serial Number'    , 'Serial Number'    , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'userId'     ,  2, 'User'  , 'User'  , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'clickTime'  ,  3, 'Time', 'Time', 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'clickForm'  ,  4, 'Menu Item Name', 'Menu Item Name', 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'clickButton',  5, 'Button Name', 'Button Name', 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'IP'         ,  6, 'Login IP'  , 'Login IP'  , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_tracking_button';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_tracking_button Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_tracking_sql.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Frank
 日期 : 2014-10-17
 內容 : app_tracking_sql
---------------------------------*/

BEGIN TRANSACTION

CREATE TABLE [dbo].[Tmp_app_tracking_sql] (
	[queryNo]  	INT IDENTITY(1,1) NOT NULL,
	[userId]   	VARCHAR(20) NOT NULL,
	[queryTime]	DATETIME NOT NULL,
	[querySql] 	VARCHAR(3000) NOT NULL,
	[IP]       	VARCHAR(40) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_tracking_sql]') AND type in (N'U'))
	EXEC sp_backup_data 'app_tracking_sql', 'Tmp_app_tracking_sql'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_tracking_sql]') AND type in (N'U'))
	DROP TABLE app_tracking_sql;	
	
EXEC sp_rename 'Tmp_app_tracking_sql', 'app_tracking_sql', 'OBJECT'
GO	

ALTER TABLE [dbo].[app_tracking_sql] ADD CONSTRAINT [PK_app_tracking_sql] PRIMARY KEY CLUSTERED
(
	[queryNo]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_tracking_sql', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_tracking_sql', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'SQL Tracking Log';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'queryNo'  ,  1, 'Serial Number', 'Serial Number', 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'userId'   ,  2, 'User'  , 'User'  , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'queryTime',  3, 'Time', 'Time', 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'querySql' ,  4, 'SQL Command', 'SQL Command', 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'IP'       ,  5, 'Login IP'  , 'Login IP'  , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_tracking_sql';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_tracking_sql Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_user.sql"  
/*---------------------------------
作者 : Frank
版本 : 1.0.0
日期 : 2017/09/18
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRY
BEGIN TRANSACTION

CREATE TABLE [dbo].[Tmp_app_user] (
    [userid]            VARCHAR(20) NOT NULL,
    [passwd]            VARCHAR(80) NOT NULL,
    [username]          VARCHAR(40) NOT NULL,
    [admins]            BIT NOT NULL,
    [position]          SMALLINT NOT NULL,
    [remark1]           VARCHAR(50) NOT NULL,
    [remark2]           VARCHAR(50) NOT NULL,
    [enabled]           BIT NOT NULL,
    [locked]            BIT NOT NULL,
    [errors]            INT NOT NULL,
    [errortime]         DATETIME NOT NULL, 
    [validthrough]      DATETIME NOT NULL,
    [valid_month]       TINYINT NOT NULL,
    [isadmin]           BIT NOT NULL,
    [deletion_date]     DATE NOT NULL,
    [deactivated_date]  DATE NOT NULL,
    [is_on_board]       BIT NOT NULL,
    [is_reg]       	BIT NOT NULL,
    [enabled_user]      VARCHAR(20) NOT NULL,
    [enabled_time]      DATETIME NOT NULL,
    [loguser]           VARCHAR(20) NOT NULL,
    [logtime]           DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects 
    WHERE object_id = OBJECT_ID(N'[dbo].[app_user]') AND type in (N'U'))
    EXEC sp_backup_data 'app_user', 'Tmp_app_user'

IF EXISTS (SELECT * FROM sys.objects
    WHERE object_id = OBJECT_ID(N'[dbo].[app_user]') AND type in (N'U'))
    DROP TABLE app_user;

EXEC sp_rename 'Tmp_app_user', 'app_user', 'OBJECT'

ALTER TABLE [dbo].[app_user] ADD 
    CONSTRAINT [PK_app_user] PRIMARY KEY  CLUSTERED 
    (
      [userid]
    )  ON [PRIMARY] 

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure') = 1)
EXEC sp_app_grant 'app_user', 'ALL';

SET NOCOUNT ON;
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_user', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'userid'          ,  1, 'User ID'           , 'User ID'         , 1, 1, 0, '', 0, 0, 0,  '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'passwd'          ,  2, 'password'          , 'password'        , 0, 0, 0, '', 0, 0, 0,  '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'username'        ,  3, 'username'          , 'username'        , 0, 0, 0, '', 0, 0, 0,  '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'admins'          ,  4, 'admins'            , 'admins'          , 0, 0, 0, '', 0, 0, 0,  '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'position'        ,  5, 'position'          , 'position'        , 0, 0, 0, '', 0, 0, 0,  '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark1'         ,  6, 'remark1'           , 'remark1'         , 0, 0, 0, '', 0, 0, 0,  '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark2'         ,  7, 'remark2'           , 'remark2'         , 0, 0, 0, '', 0, 0, 0,  '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'enabled'         ,  8, 'Is account enabled', 'enabled'         , 0, 0, 0, '', 0, 0, 0, '0', 1,  8, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'locked'          ,  9, 'Is account locked' , 'locked'          , 0, 0, 0, '', 0, 0, 0, '0', 1,  9, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'errors'          , 10, 'errors'            , 'errors'          , 0, 0, 0, '', 0, 0, 0, '0', 1, 10, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'errortime'       , 11, 'errortime'         , 'errortime'       , 0, 0, 0, '', 0, 0, 0, '0', 1, 11, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'validthrough'    , 12, 'validthrough'      , 'validthrough'    , 0, 0, 0, '', 0, 0, 0,  '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'valid_month'     , 13, 'Valid Month'       , 'Valid Month'     , 0, 0, 0, '', 0, 0, 0,  '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'isadmin'         , 14, 'Is Admin'          , 'Is Admin'        , 0, 0, 0, '', 0, 0, 0,  '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'deletion_date'   , 15, 'Deletion Date'     , 'Deletion Date'   , 0, 0, 0, '', 0, 0, 0,  '', 1, 16, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'deactivated_date', 16, 'Deactivated Date'  , 'Deactivated Date', 0, 0, 0, '', 0, 0, 0,  '', 1, 16, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_on_board'     , 17, 'Onboarding Staff'  , 'Onboarding Staff', 0, 0, 0, '', 0, 0, 0,  '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_reg'          , 18, 'Is Reg'            , 'Is Reg'          , 0, 0, 0, '', 0, 0, 0,  '', 1, 18, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'enabled_user'    , 19, 'Enabled User'      , 'Enabled User'    , 0, 0, 0, '', 0, 0, 0,  '', 1, 19, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'enabled_time'    , 20, 'Enabled Time'      , 'Enabled Time'    , 0, 0, 0, '', 0, 0, 0,  '', 1, 20, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'         , 21, 'Loguser'           , 'Loguser'         , 0, 0, 0, '', 0, 0, 0,  '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'         , 22, 'Logtime'           , 'Logtime'         , 0, 0, 0, '', 0, 0, 0,  '', 1, 22, 150, 'DateEdit', @loguser, @dt;

IF @owfield = 1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 

  UPDATE a SET a.field_idx = c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_user';  

  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 


IF @owoption = 1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND opt_no = a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
COMMIT
PRINT '更新 app_user 結束!' 
END TRY
BEGIN CATCH 
    ROLLBACK 
    DECLARE @errormsg VARCHAR (500)
    SELECT @errormsg = errormessage FROM fn_error_info()
    PRINT '更新 app_user 失敗 : ' + @errormsg

END CATCH
GO 
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_userandrole.sql"  
/*---------------------------------
版本 : 1.0.0
日期 : 2014/7/22
內容 : New Version
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION

CREATE TABLE [dbo].[Tmp_app_userandrole] (
	[parentkey]     INT NOT NULL,
	[childkey]      INT NOT NULL,
	[parentid]		VARCHAR(20) NOT NULL,
	[childid]		VARCHAR(20) NOT NULL,
	[loguser]		VARCHAR(20) NOT NULL,
	[logtime]		DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_userandrole]') AND type in (N'U'))
	EXEC sp_backup_data 'app_userandrole', 'Tmp_app_userandrole'

IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_userandrole]') AND type in (N'U'))
	DROP TABLE app_userandrole;

EXEC sp_rename 'Tmp_app_userandrole', 'app_userandrole', 'OBJECT'
GO

ALTER TABLE [dbo].[app_userandrole] ADD 
	CONSTRAINT [PK_app_userandgroup] PRIMARY KEY  CLUSTERED 
	(
		[parentkey], [childkey], [parentid], [childid]
	)  ON [PRIMARY] 
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure') = 1)
EXEC sp_app_grant 'app_userandrole', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_userandrole', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'parentkey', 1, 'parentkey', 'parentkey', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'childkey', 2, 'childkey', 'childkey', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'parentid', 3, 'parentid', 'parentid', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'childid', 4, 'childid', 'childid', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser', 11, '異動人員', '異動人員', 0, 0, 0, '', 0, 0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime', 12, '異動時間', '異動時間', 0, 0, 0, '', 0, 0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
IF @owfield = 1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 

  UPDATE a SET a.field_idx = c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_userandrole';  

  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption = 1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND opt_no = a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_userandrole 結束!' 
GO 
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_userloglist.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 吳欣融
 日期 : 2014-06-11
 內容 : app_userloglist
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_userloglist] (
	[userid]    	VARCHAR(20) NOT NULL,
	[logintime] 	DATETIME NOT NULL,
	[logouttime]	DATETIME NOT NULL,
	[log_result]    SMALLINT NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_userloglist]') AND type in (N'U'))
	EXEC sp_backup_data 'app_userloglist', 'Tmp_app_userloglist'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_userloglist]') AND type in (N'U'))
	DROP TABLE app_userloglist;

EXEC sp_rename 'Tmp_app_userloglist', 'app_userloglist', 'OBJECT'
GO

ALTER TABLE [dbo].[app_userloglist] ADD CONSTRAINT [PK_app_userloglist] PRIMARY KEY CLUSTERED
(
	[userid],[logintime]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_userloglist', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_userloglist', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'User Log List';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'userid'    ,  1, 'User', 'User', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logintime' ,  2, 'Login Time', 'Login Time', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logouttime',  3, 'Logout Time', 'Logout Time', 0, 0, 0, '', 0,   903, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'log_result',  4, 'Log Result', 'Log Result', 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_userloglist';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_userloglist Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_user_transfer_log.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 吳欣融
 日期 : 2014-06-11
 內容 : app_user_transfer_log
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_user_transfer_log] (
    [userid]          VARCHAR(20) NOT NULL,
    [transfer_index]  INT NOT NULL,
    [groupid]         VARCHAR(20) NOT NULL,
    [groupkey]        INT NOT NULL,
    [loguser]         VARCHAR(20) NOT NULL,
    [logtime]         DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_user_transfer_log]') AND type in (N'U'))
    EXEC sp_backup_data 'app_user_transfer_log', 'Tmp_app_user_transfer_log'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_user_transfer_log]') AND type in (N'U'))
    DROP TABLE app_user_transfer_log;

EXEC sp_rename 'Tmp_app_user_transfer_log', 'app_user_transfer_log', 'OBJECT'
GO

ALTER TABLE [dbo].[app_user_transfer_log] ADD CONSTRAINT [PK_app_user_transfer_log] PRIMARY KEY CLUSTERED
(
    [userid],[transfer_index]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'app_user_transfer_log', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_user_transfer_log', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'User Log List';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'userid'        ,  1, 'User ID'       , 'User ID'       , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'transfer_index',  2, 'Transfer Index', 'Transfer Index', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'groupid'       ,  3, 'Group ID'      , 'Group ID'      , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'groupkey'      ,  3, 'Group Key'     , 'Group Key'     , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'       ,  4, 'Log User'      , 'Log User'      , 0, 0, 0, '', 0,   0, 0, '', 0, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'       ,  5, 'Log Time'      , 'Log Time'      , 0, 0, 0, '', 0,   0, 0, '', 0, 17, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_user_transfer_log';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_user_transfer_log Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\app_winuser.sql"  
/*---------------------------------
版本 : 1.0.1
日期 : 2014/7/22
內容 : New Version
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION

CREATE TABLE [dbo].[Tmp_app_winuser] (
	[userid]    VARCHAR(20) NOT NULL,
	[winuser]   VARCHAR(20) NOT NULL,
	[domain]    VARCHAR(20) NOT NULL,
	[fullname]  VARCHAR(100) NOT NULL,
	[position]  VARCHAR(50) NOT NULL,
	[lock]      BIT NOT NULL,
	[lockuser]  VARCHAR(20) NOT NULL,
	[locktime]  DATETIME NOT NULL,
	[loguser]   VARCHAR(20) NOT NULL,
	[logtime]   DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_winuser]') AND type in (N'U'))
	EXEC sp_backup_data 'app_winuser', 'Tmp_app_winuser'


IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_winuser]') AND type in (N'U'))
	DROP TABLE app_winuser;

EXEC sp_rename 'Tmp_app_winuser', 'app_winuser', 'OBJECT'
GO

ALTER TABLE [dbo].[app_winuser] ADD 
	CONSTRAINT [PK_app_winuser] PRIMARY KEY  CLUSTERED 
	(
	  [userid],
	  [winuser],
	  [domain]
	)  ON [PRIMARY] 
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure') = 1)
EXEC sp_app_grant 'app_winuser', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_winuser', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'userid', 1, '帳號', 'userid', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'winuser', 2, 'WIN使用者', 'winuser', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'domain', 3, '網域名稱', 'domain', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fullname', 4, 'WIN使用者名稱', 'fullname', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'position', 5, 'WIN使用者職稱', 'position', 0, 0, 0, '', 0, 0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lock', 6, '確認', '確認', 0, 0, 0, '', 0, 0, 0, 'False', 1, 6, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lockuser', 7, '確認人員', '確認人員', 0, 0, 0, '', 0, 0, 0, '', 1, 7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'locktime', 8, '確認時間', '確認時間', 0, 0, 0, '', 0, 0, 0, '', 1, 8, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser', 9, '異動人員', '異動人員', 0, 0, 0, '', 0, 0, 0, '', 1, 9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime', 10, '異動時間', '異動時間', 0, 0, 0, '', 0, 0, 0, '', 1, 10, 150, 'DateEdit', @loguser, @dt;
IF @owfield = 1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 

  UPDATE a SET a.field_idx = c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_winuser';  

  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption = 1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE pno = a.pno AND opt_no = a.opt_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_winuser 結束!' 
GO 
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\board.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000269
 日期 : 2014-06-05
 內容 : board
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_board] (
	[number]  	INT NOT NULL,
	[content] 	NVARCHAR(200) NOT NULL,
	[fromTime]	DATETIME NOT NULL,
	[toTime]  	DATETIME NOT NULL,
	[light]   	SMALLINT NOT NULL,
	[note]    	NVARCHAR(50) NOT NULL,
	[loguser] 	VARCHAR(20) NOT NULL,
	[logtime] 	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[board]') AND type in (N'U'))
	EXEC sp_backup_data 'board', 'Tmp_board'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[board]') AND type in (N'U'))
	DROP TABLE board;

EXEC sp_rename 'Tmp_board', 'board', 'OBJECT'
GO

ALTER TABLE [dbo].[board] ADD CONSTRAINT [PK_board] PRIMARY KEY CLUSTERED
(
	[number]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'board', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'board', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '佈告欄';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'number'  ,  1, 'Index'    , 'Index'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'content' ,  2, 'Content'  , 'Content'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fromTime',  3, 'Starting time', 'Starting time', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'toTime'  ,  4, 'End Time', 'End Time', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'light'   ,  5, 'Light'    , 'Light'    , 0, 0, 0, '', 0,  0, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'    ,  6, 'Notes'    , 'Notes'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser' ,  7, 'Loguser', 'Loguser', 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime' ,  8, 'Logtime', 'Logtime', 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'board';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table board Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\log_table.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/6/14
 內容 : log_table()
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_log_table] (
	[tablename]		VARCHAR(50) NOT NULL,
	[chinese]		VARCHAR(50) NOT NULL,
	[english]		VARCHAR(50) NOT NULL,
	[recording]		BIT NOT NULL,
	[note]		VARCHAR(200) NOT NULL,
	[loguser]		VARCHAR(20) NOT NULL,
	[logtime]		DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[log_table]') AND type in (N'U'))
	EXEC sp_backup_data 'log_table', 'Tmp_log_table'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[log_table]') AND type in (N'U'))
	DROP TABLE log_table;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_log_table', 'log_table', 'OBJECT'
GO

ALTER TABLE [dbo].[log_table] ADD 
	CONSTRAINT [PK_log_table] PRIMARY KEY  CLUSTERED 
	(
	  [tablename]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'log_table', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'log_table', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'log_table';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 log_table 結束!' 
GO 
SET ANSI_PADDING OFF
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\SystemInitial\table\log_table_field.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/6/14
 內容 : log_table_field()
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_log_table_field] (
	[tablename]		VARCHAR(50) NOT NULL,
	[fieldname]		VARCHAR(50) NOT NULL,
	[idx]		INT NOT NULL,
	[chinese]		VARCHAR(50) NOT NULL,
	[english]		VARCHAR(50) NOT NULL,
	[recording]		BIT NOT NULL,
	[loguser]		VARCHAR(20) NOT NULL,
	[logtime]		DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[log_table_field]') AND type in (N'U'))
	EXEC sp_backup_data 'log_table_field', 'Tmp_log_table_field'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[log_table_field]') AND type in (N'U'))
	DROP TABLE log_table_field;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_log_table_field', 'log_table_field', 'OBJECT'
GO

ALTER TABLE [dbo].[log_table_field] ADD 
	CONSTRAINT [PK_log_table_field] PRIMARY KEY  CLUSTERED 
	(
	  [tablename],
	  [fieldname]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'log_table_field', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'log_table_field', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'log_table_field';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 log_table_field 結束!' 
GO 
SET ANSI_PADDING OFF
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_db.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/5/11
 內容 : app_etl_db()
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_db] (
    [name]              VARCHAR(20) NOT NULL,
    [server]            VARCHAR(40) NOT NULL,
    [db_name]           VARCHAR(30) NOT NULL,
    [userid]            VARCHAR(30) NOT NULL,
    [psw]               VARCHAR(100) NOT NULL,
    [dbtype]            SMALLINT NOT NULL,
    [is_password_fixed] BIT NOT NULL,
    [loguser]           VARCHAR(20) NOT NULL,
    [logtime]           DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_db]') AND type in (N'U'))
    EXEC sp_backup_data 'app_etl_db', 'Tmp_app_etl_db'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_db]') AND type in (N'U'))
    DROP TABLE app_etl_db;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_db', 'app_etl_db', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_db] ADD 
    CONSTRAINT [PK_app_imp_db] PRIMARY KEY  CLUSTERED 
    (
      [name]
    )  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_etl_db', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_etl_db', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'name'             , 1, 'Connection name', 'Connection name', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'server'           , 2, 'Server', 'Server', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'db_name'          , 3, 'Database', 'Database', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'userid'           , 4, 'User ID', 'User ID', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'psw'              , 5, 'Password', 'Password', 0, 0, 0, '', 0, 0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'dbtype'           , 6, 'Database Type', 'Database Type', 0, 0, 0, '', 0, 101, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_password_fixed', 6, 'Is password fixed', 'Is password fixed', 0, 0, 0, '', 0, 0, 0, '', 1, 5, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'          , 7, 'Log User', 'Log User', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'          , 8, 'Log Time', 'Log Time', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;


IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_db';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
  
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_etl_db 結束!' 
GO 

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_deliver_detail.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2016-03-02
 內容 : app_etl_deliver_detail
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_etl_deliver_detail] (
	[set_id]   	VARCHAR(20) NOT NULL,
	[file_type]	SMALLINT NOT NULL,
	[file_id]  	VARCHAR(36) NOT NULL,
	[file_name]	VARCHAR(255) NOT NULL,
	[loguser]  	VARCHAR(20) NOT NULL,
	[logtime]  	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_deliver_detail]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_deliver_detail', 'Tmp_app_etl_deliver_detail'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_deliver_detail]') AND type in (N'U'))
	DROP TABLE app_etl_deliver_detail;

EXEC sp_rename 'Tmp_app_etl_deliver_detail', 'app_etl_deliver_detail', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_deliver_detail] ADD CONSTRAINT [PK_app_etl_deliver_detail] PRIMARY KEY CLUSTERED
(
	[set_id],[file_type],[file_id]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_etl_deliver_detail', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_deliver_detail', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'ETL發送明細檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'set_id'   ,  1, '設定代碼', '設定代碼', 1, 1, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_type',  2, '檔案類型', '檔案類型', 1, 1, 0, '', 0,10004, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_id'  ,  3, '檔案代碼', '檔案代碼', 1, 1, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_name',  4, '檔案名稱', '檔案名稱', 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'  ,  5, '異動人員', '異動人員', 0, 0, 0, '', 0,    0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'  ,  6, '異動時間', '異動時間', 0, 0, 0, '', 0,    0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_deliver_detail';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_etl_deliver_detail Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_deliver_setting.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2016-03-02
 內容 : app_etl_deliver_setting
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_etl_deliver_setting] (
	[id]                  	VARCHAR(20) NOT NULL,
	[name]                	VARCHAR(40) NOT NULL,
	[file_name]           	VARCHAR(255) NOT NULL,
	[is_zip]              	BIT NOT NULL,
	[zip_password]        	VARCHAR(100) NOT NULL,
	[ftp_server_id]       	VARCHAR(20) NOT NULL,
	[ftp_remote_file_name]	VARCHAR(255) NOT NULL,
	[email_accounts]      	VARCHAR(300) NOT NULL,
	[email_subject]       	VARCHAR(100) NOT NULL,
	[email_content]       	VARCHAR(MAX) NOT NULL,
	[loguser]             	VARCHAR(20) NOT NULL,
	[logtime]             	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_deliver_setting]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_deliver_setting', 'Tmp_app_etl_deliver_setting'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_deliver_setting]') AND type in (N'U'))
	DROP TABLE app_etl_deliver_setting;

EXEC sp_rename 'Tmp_app_etl_deliver_setting', 'app_etl_deliver_setting', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_deliver_setting] ADD CONSTRAINT [PK_app_etl_deliver_setting] PRIMARY KEY CLUSTERED
(
	[id]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_etl_deliver_setting', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_deliver_setting', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'ETL發送設定檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'id'                  ,  1, '設定代碼'        , '設定代碼'        , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'                ,  2, '設定名稱'        , '設定名稱'        , 0, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_name'           ,  3, '傳送檔案名稱'    , '傳送檔案名稱'    , 0, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_zip'              ,  4, '是否壓縮'        , '是否壓縮'        , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'zip_password'        ,  5, '壓縮密碼'        , '壓縮密碼'        , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ftp_server_id'       ,  6, 'FTP server代碼'  , 'FTP server代碼'  , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ftp_remote_file_name',  7, 'FTP遠端檔案名稱' , 'FTP遠端檔案名稱' , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'email_accounts'      ,  8, '寄送帳號'        , '寄送帳號'        , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'email_subject'       ,  9, '信件標題'        , '信件標題'        , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'email_content'       , 10, '信件內容'        , '信件內容'        , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'MemoEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'             , 11, '異動人員'        , '異動人員'        , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'             , 12, '異動時間'        , '異動時間'        , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_deliver_setting';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_etl_deliver_setting Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_email_ldap.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2016-03-02
 內容 : app_etl_email_ldap
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_etl_email_ldap] (
	[email]   	VARCHAR(100) NOT NULL,
	[username]	VARCHAR(100) NOT NULL,
	[password]	VARCHAR(100) NOT NULL,
	[domain]  	VARCHAR(255) NOT NULL,
	[loguser] 	VARCHAR(20) NOT NULL,
	[logtime] 	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_email_ldap]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_email_ldap', 'Tmp_app_etl_email_ldap'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_email_ldap]') AND type in (N'U'))
	DROP TABLE app_etl_email_ldap;

EXEC sp_rename 'Tmp_app_etl_email_ldap', 'app_etl_email_ldap', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_email_ldap] ADD CONSTRAINT [PK_app_etl_email_ldap] PRIMARY KEY CLUSTERED
(
	[email]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_etl_email_ldap', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_email_ldap', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Email LDAP檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'email'   ,  1, 'Email'   , 'Email'   , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'username',  2, 'LDAP帳號', 'LDAP帳號', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'password',  3, 'LDAP密碼', 'LDAP密碼', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'domain'  ,  4, 'LDAP網域', 'LDAP網域', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser' ,  5, '異動人員', '異動人員', 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime' ,  6, '異動時間', '異動時間', 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_email_ldap';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_etl_email_ldap Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_export.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2016-03-02
 內容 : app_etl_export
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_etl_export] (
	[id]         	VARCHAR(20) NOT NULL,
	[name]       	VARCHAR(40) NOT NULL,
	[file_name]  	VARCHAR(255) NOT NULL,
	[file_type]  	SMALLINT NOT NULL,
	[query_sql]  	VARCHAR(MAX) NOT NULL,
	[check_sql]  	VARCHAR(MAX) NOT NULL,
	[check_type] 	SMALLINT NOT NULL,
	[has_caption]	BIT NOT NULL,
	[start_index]	INT NOT NULL,
	[template]   	VARCHAR(1000) NOT NULL,
	[txt_separator] VARCHAR(20) NOT NULL,
	[codepage]   	SMALLINT NOT NULL,
	[loguser]    	VARCHAR(20) NOT NULL,
	[logtime]    	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_export]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_export', 'Tmp_app_etl_export'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_export]') AND type in (N'U'))
	DROP TABLE app_etl_export;

EXEC sp_rename 'Tmp_app_etl_export', 'app_etl_export', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_export] ADD CONSTRAINT [PK_app_etl_export] PRIMARY KEY CLUSTERED
(
	[id]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_etl_export', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_export', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'ETL匯出資料檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'id'            ,  1, '代碼'            , '代碼'            , 1, 1, 0, '', 0,    0,  0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'          ,  2, '名稱'            , '名稱'            , 0, 1, 0, '', 0,    0,  0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_name'     ,  3, '匯出檔案名稱'    , '匯出檔案名稱'    , 0, 1, 0, '', 0,    0,  0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_type'     ,  4, '匯出檔案格式'    , '匯出檔案格式'    , 0, 1, 0, '', 0,10006,  0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'query_sql'     ,  5, '查詢語法'        , '查詢語法'        , 0, 0, 0, '', 0,    0,  0, '', 1, 1, 150, 'MemoEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'check_sql'     ,  6, '檢核語法'        , '檢核語法'        , 0, 0, 0, '', 0,    0,  0, '', 1, 1, 150, 'MemoEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'check_type'    ,  7, '檢核類型'        , '檢核類型'        , 0, 0, 0, '', 0,10003,  0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'has_caption'   ,  8, '是否匯出欄位名稱', '是否匯出欄位名稱', 0, 0, 0, '', 0,    0,  0, '', 1, 1, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'start_index'   ,  9, '起始列數'        , '起始列數'        , 0, 0, 0, '', 0,    0, 10, '', 1, 1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'template'      , 10, 'Excel匯出範本'   , 'Excel匯出範本'   , 0, 0, 0, '', 0,    0,  0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'txt_separator' , 11, 'txt分隔字元'     , 'txt分隔字元'     , 0, 0, 0, '', 0,    0,  0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'codepage'      , 12, '匯出編碼格式'    , '匯出編碼格式'    , 0, 0, 0, '', 0,10008,  0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'       , 13, '異動人員'        , '異動人員'        , 0, 0, 0, '', 0,    0,  0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'       , 14, '異動時間'        , '異動時間'        , 0, 0, 0, '', 0,    0,  0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_export';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_etl_export Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_export_txt.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2016-04-14
 內容 : app_etl_export_txt
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_etl_export_txt] (
	[id]           	VARCHAR(20) NOT NULL,
	[col_name]     	VARCHAR(40) NOT NULL,
	[cname]        	VARCHAR(100) NOT NULL,
	[col_type]     	SMALLINT NOT NULL,
	[txt_length]   	INT NOT NULL,
	[pad_char]      VARCHAR(1) NOT NULL,
	[number_length]	VARCHAR(10) NOT NULL,
	[number_sign]  	VARCHAR(2) NOT NULL,
	[date_format]  	SMALLINT NOT NULL,
	[idx]           INT NOT NULL,
	[default_value] VARCHAR(100) NOT NULL,
	[loguser]      	VARCHAR(20) NOT NULL,
	[logtime]      	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_export_txt]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_export_txt', 'Tmp_app_etl_export_txt'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_export_txt]') AND type in (N'U'))
	DROP TABLE app_etl_export_txt;

EXEC sp_rename 'Tmp_app_etl_export_txt', 'app_etl_export_txt', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_export_txt] ADD CONSTRAINT [PK_app_etl_export_txt] PRIMARY KEY CLUSTERED
(
	[id],[col_name]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_etl_export_txt', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_export_txt', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'ETL匯出文字設定檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'id'           ,  1, '代碼'          , '代碼'          , 1, 1, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'col_name'     ,  2, '欄位'          , '欄位'          , 1, 1, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname'        ,  3, '中文名稱'      , '中文名稱'      , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'col_type'     ,  4, '欄位類型'      , '欄位類型'      , 0, 0, 0, '', 0,10002, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'txt_length'   ,  5, '文字長度(byte)', '文字長度(byte)', 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'pad_char'     ,  6, '填補字元'      , '填補字元'      , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'number_length',  7, '數字長度'      , '數字長度'      , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'number_sign'  ,  8, '正負號顯示字元', '正負號顯示字元', 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date_format'  ,  9, '日期格式'      , '日期格式'      , 0, 0, 0, '', 0,10001, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'idx'          , 10, '欄位順序'      , '欄位順序'      , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'default_value', 11, '預設值'        , '預設值'        , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'      , 12, '異動人員'      , '異動人員'      , 0, 0, 0, '', 0,    0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'      , 13, '異動時間'      , '異動時間'      , 0, 0, 0, '', 0,    0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_export_txt';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_etl_export_txt Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_ftp_server.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2016-03-02
 內容 : app_etl_ftp_server
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_etl_ftp_server] (
	[id]        	VARCHAR(20) NOT NULL,
	[name]      	VARCHAR(40) NOT NULL,
	[username]  	VARCHAR(40) NOT NULL,
	[password]  	VARCHAR(100) NOT NULL,
	[host]      	VARCHAR(100) NOT NULL,
	[port]      	INT NOT NULL,
	[is_passive]	BIT NOT NULL,
	[loguser]   	VARCHAR(20) NOT NULL,
	[logtime]   	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_ftp_server]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_ftp_server', 'Tmp_app_etl_ftp_server'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_ftp_server]') AND type in (N'U'))
	DROP TABLE app_etl_ftp_server;

EXEC sp_rename 'Tmp_app_etl_ftp_server', 'app_etl_ftp_server', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_ftp_server] ADD CONSTRAINT [PK_app_etl_ftp_server] PRIMARY KEY CLUSTERED
(
	[id]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_etl_ftp_server', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_ftp_server', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'FTP Server設定檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'id'        ,  1, '設定代碼'      , '設定代碼'      , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'      ,  2, '設定名稱'      , '設定名稱'      , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'username'  ,  3, '登入帳號'      , '登入帳號'      , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'password'  ,  4, '登入密碼'      , '登入密碼'      , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'host'      ,  5, '主機'          , '主機'          , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'port'      ,  6, '埠號'          , '埠號'          , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_passive',  7, '是否為被動模式', '是否為被動模式', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'   ,  8, '異動人員'      , '異動人員'      , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'   ,  9, '異動時間'      , '異動時間'      , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_ftp_server';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_etl_ftp_server Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_import_data.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2016-03-02
 內容 : app_etl_import_data
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_etl_import_data] (
	[id]             	VARCHAR(20) NOT NULL,
	[source_type]    	SMALLINT NOT NULL,
	[name]           	VARCHAR(40) NOT NULL,
	[email]          	VARCHAR(100) NOT NULL,
	[subject_filter] 	VARCHAR(100) NOT NULL,
	[attach_filter]  	VARCHAR(100) NOT NULL,
	[ftp_server_id]  	VARCHAR(20) NOT NULL,
	[ftp_remote_file]	VARCHAR(255) NOT NULL,
	[file_path]      	VARCHAR(255) NOT NULL,
	[is_unzip]       	BIT NOT NULL,
	[unzip_password] 	VARCHAR(100) NOT NULL,
	[unzip_file_path] 	VARCHAR(255) NOT NULL,
	[transform_type]    SMALLINT NOT NULL,
	[loguser]        	VARCHAR(20) NOT NULL,
	[logtime]        	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_import_data]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_import_data', 'Tmp_app_etl_import_data'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_import_data]') AND type in (N'U'))
	DROP TABLE app_etl_import_data;

EXEC sp_rename 'Tmp_app_etl_import_data', 'app_etl_import_data', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_import_data] ADD CONSTRAINT [PK_app_etl_import_data] PRIMARY KEY CLUSTERED
(
	[id]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_etl_import_data', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_import_data', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'ETL匯入來源資料檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'id'             ,  1, '設定代碼'      , '設定代碼'      , 1, 1, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source_type'    ,  2, '來源類型'      , '來源類型'      , 0, 0, 0, '', 0,10005, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'           ,  3, '設定名稱'      , '設定名稱'      , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'email'          ,  4, '下載帳號'      , '下載帳號'      , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'subject_filter' ,  5, '信件標題關鍵字', '信件標題關鍵字', 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'attach_filter'  ,  6, '附檔關鍵字'    , '附檔關鍵字'    , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ftp_server_id'  ,  7, 'FTP Server代碼', 'FTP Server代碼', 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ftp_remote_file',  8, 'FTP遠端檔案'   , 'FTP遠端檔案'   , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_path'      ,  9, '下載儲存檔名'  , '下載儲存檔名'  , 0, 1, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_unzip'       , 10, '是否解壓縮'    , '是否解壓縮'    , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'unzip_password' , 11, '解壓縮密碼'    , '解壓縮密碼'    , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'unzip_file_path', 12, '解壓縮後檔名'  , '解壓縮後檔名'  , 0, 0, 0, '', 0,    0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'transform_type' , 13, '來源檔案類型'  , '來源檔案類型'  , 0, 0, 0, '', 0,10007, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'        , 14, '異動人員'      , '異動人員'      , 0, 0, 0, '', 0,    0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'        , 15, '異動時間'      , '異動時間'      , 0, 0, 0, '', 0,    0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_import_data';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_etl_import_data Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_jobdef.sql"  
/*---------------------------------
版本 : 1.0.2
日期 : 2015/2/12
內容 : 新增群組收信名單
版本 : 1.0.1
日期 : 2014/6/9
內容 : 新增作業日期行事曆國別
版本 : 1.0.0
日期 : 2012/5/14
內容 : app_etl_jobdef
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_jobdef] (
    [jobindex]          INT NOT NULL,
    [jobname]           VARCHAR(50) NOT NULL,
    [itempos]           VARCHAR(15) NOT NULL,
    [jobcalendar]       VARCHAR(10) NOT NULL,
    [jobnote]           VARCHAR(100) NOT NULL,
    [recipient]         VARCHAR(200) NOT NULL,
    [loguser]           VARCHAR(20) NOT NULL,
    [logtime]           DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_jobdef]') AND type in (N'U'))
    EXEC sp_backup_data 'app_etl_jobdef', 'Tmp_app_etl_jobdef'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_jobdef]') AND type in (N'U'))
    DROP TABLE app_etl_jobdef;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_jobdef', 'app_etl_jobdef', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_jobdef] ADD 
    CONSTRAINT [PK_app_etl_jobdef] PRIMARY KEY  CLUSTERED 
    (
      [jobindex]
    )  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_etl_jobdef', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_etl_jobdef', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '匯入作業設定'; 
    SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
    INSERT #appTableField SELECT @tbname, 'jobindex'   , 1, 'Job Index', 'Job Index', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'jobname'    , 2, 'Job Name', 'Job Name', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'itempos'    , 3, 'Menu Position', 'Menu Position', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'jobcalendar', 4, 'Job Calendar', 'Job Calendar', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'jobnote'    , 4, 'Note', 'Note', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'recipient'  , 4, 'Recipient', 'Recipient', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'loguser'    , 5, 'Log User', 'Log User', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'logtime'    , 6, 'Log Time', 'Log Time', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;

    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
    DROP TABLE #appTableField; 
    
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_jobdef';  
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_etl_jobdef 結束!' 
GO 
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_joblist.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/5/14
 內容 : app_etl_joblist
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_joblist] (
    [jobindex]           INT NOT NULL,
    [type]               SMALLINT NOT NULL,
    [id]                 VARCHAR(20) NOT NULL,
    [seq]                INT NOT NULL,
    [impfilename]        VARCHAR(100) NOT NULL,
    [rundatetp]          SMALLINT NOT NULL,
    [mail_ok]            VARCHAR(200) NOT NULL,
    [mail_error]         VARCHAR(200) NOT NULL,
    [loguser]            VARCHAR(20) NOT NULL,
    [logtime]            DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_joblist]') AND type in (N'U'))
    EXEC sp_backup_data 'app_etl_joblist', 'Tmp_app_etl_joblist'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_joblist]') AND type in (N'U'))
    DROP TABLE app_etl_joblist;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_joblist', 'app_etl_joblist', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_joblist] ADD 
    CONSTRAINT [PK_app_etl_joblist] PRIMARY KEY  CLUSTERED 
    (
      [jobindex],
      [type],
      [id]
    )  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_etl_joblist', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_etl_joblist', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '匯入作業明細'; 
    SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
    INSERT #appTableField SELECT @tbname, 'jobindex'   , 1, 'Job Index', 'Job Index', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'type'       , 2, 'Type', 'Type', 0, 0, 0, '', 0, 104, 0, '', 1, 2, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'id'         , 3, 'ID', 'ID', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'seq'        , 4, 'Execution Sequence', 'Execution Sequence', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'impfilename', 5, 'File Name', 'File Name', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'rundatetp'  , 6, 'Run Date Type', 'Run Date Type', 0, 0, 0, '', 0, 107, 0, '', 1, 2, 150, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'mail_ok'    , 7, 'Success Mail Recipient', 'Success Mail Recipient', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'mail_error' , 8, 'Error Mail Recipient', 'Error Mail Recipient', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;    
    INSERT #appTableField SELECT @tbname, 'loguser'    , 9, 'Log User', 'Log User', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'logtime'    , 10, 'Log Time', 'Log Time', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;

    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
    DROP TABLE #appTableField; 
    
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_joblist';  
     
----更新欄位選項及說明 
--  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
--  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 

--IF @owoption=1 
--  BEGIN 
--    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
--    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
--    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
--    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
--  END ELSE BEGIN 
--    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
--       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
--    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
--       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
--  END;  
--  DROP TABLE #appTableFieldo, #appTableFieldoi; 
     
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_etl_joblist 結束!' 
GO 
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_mapingcode.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/5/14
 內容 : app_etl_mapingcode
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_mapingcode] (
    [mapcode]           VARCHAR(20) NOT NULL,
    [mapname]           VARCHAR(40) NOT NULL,
    [maptype]           SMALLINT NOT NULL,
    [maptable]          VARCHAR(40) NOT NULL,
    [keyfield]          VARCHAR(40) NOT NULL,
    [valuefield]        VARCHAR(40) NOT NULL,
    [note]              VARCHAR(100) NOT NULL,
    [dvalue]            VARCHAR(100) NOT NULL,
    [loguser]           VARCHAR(20) NOT NULL,
    [logtime]           DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_mapingcode]') AND type in (N'U'))
    EXEC sp_backup_data 'app_etl_mapingcode', 'Tmp_app_etl_mapingcode'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_mapingcode]') AND type in (N'U'))
    DROP TABLE app_etl_mapingcode;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_mapingcode', 'app_etl_mapingcode', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_mapingcode] ADD 
    CONSTRAINT [PK_app_etl_mapingcode] PRIMARY KEY  CLUSTERED 
    (
      [mapcode]
    )  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_etl_mapingcode', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_etl_mapingcode', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, '轉碼代碼檔'; 
    SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
    INSERT #appTableField SELECT @tbname, 'mapcode'   , 1, 'Code', 'Code', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'mapname'   , 2, 'Name', 'Name', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'maptype'   , 3, 'Type', 'Type', 0, 0, 0, '', 0, 105, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'maptable'  , 3, 'Table', 'Table', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'keyfield'  , 3, 'Query Field', 'Query Field', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'valuefield', 3, 'Return Field', 'Return Field', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'note'      , 3, 'Note', 'Note', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'dvalue'    , 4, 'Default Value', 'Default Value', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'loguser'   , 5, 'Log User', 'Log User', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'logtime'   , 6, 'Log Time', 'Log Time', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;

    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
    DROP TABLE #appTableField; 
    
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_mapingcode';  
     
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 

IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 

 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_etl_mapingcode 結束!' 
GO 
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_mapinglist.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/5/14
 內容 : app_etl_mapinglist
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_mapinglist] (
    [mapcode]             VARCHAR(20) NOT NULL,
    [impvalue]            VARCHAR(100) NOT NULL,
    [outvalue]            VARCHAR(100) NOT NULL,
    [loguser]             VARCHAR(20) NOT NULL,
    [logtime]             DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_mapinglist]') AND type in (N'U'))
    EXEC sp_backup_data 'app_etl_mapinglist', 'Tmp_app_etl_mapinglist'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
    WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_mapinglist]') AND type in (N'U'))
    DROP TABLE app_etl_mapinglist;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_mapinglist', 'app_etl_mapinglist', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_mapinglist] ADD 
    CONSTRAINT [PK_app_etl_mapinglist] PRIMARY KEY  CLUSTERED 
    (
      [mapcode],
      [impvalue]
    )  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_etl_mapinglist', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_etl_mapinglist', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
    SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
    INSERT #appTableField SELECT @tbname, 'mapcode', 1, 'Code', 'Code', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'impvalue', 2, 'Source Value', 'Source Value', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'outvalue', 3, 'Target Value', 'Target Value', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'loguser', 4, 'Log User', 'Log User', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
    INSERT #appTableField SELECT @tbname, 'logtime', 5, 'Log Time', 'Log Time', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;

    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
    DROP TABLE #appTableField; 
    
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_mapinglist';  

 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_etl_mapinglist 結束!' 
GO 
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_report_control.sql"  
--this script is created by SpecCreator
/*---------------------------------
 版本 : 1
 日期 : 2016-04-14 
 內容 : app_etl_report_control
---------------------------------*/
BEGIN TRANSACTION 

--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_report_control] (
    [id]            VARCHAR(20) NOT NULL,
    [control]       VARCHAR(50) NOT NULL,
    [name]          VARCHAR(50) NOT NULL,
    [type]          SMALLINT NOT NULL,
    [date_type]     SMALLINT NOT NULL,
    [value_type]    SMALLINT NOT NULL,
    [value]         VARCHAR(50) NOT NULL,
    [value_text]    NVARCHAR(50) NOT NULL,
    [loguser]       VARCHAR(20) NOT NULL,
    [logtime]       DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_report_control]') AND type in (N'U'))
    EXEC sp_backup_data 'app_etl_report_control', 'Tmp_app_etl_report_control'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_report_control]') AND type in (N'U'))
    DROP TABLE app_etl_report_control;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_report_control', 'app_etl_report_control', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_report_control] ADD CONSTRAINT [PK_app_etl_report_control] PRIMARY KEY CLUSTERED
(
    [id],[control]
)   
ON [PRIMARY]
GO

--6.完成(買單).....
COMMIT;

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'app_etl_report_control', 'ALL';

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_report_control', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '報表控制項設定';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'id'        ,  1, 'ID', 'ID', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'control'   ,  2, 'Control Name'  , 'Control Name'  , 1, 1, 0, '', 0,   0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'      ,  3, 'Name'    , 'Name'    , 0, 0, 0, '', 0,   0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'type'      ,  4, 'Type'  , 'Type'  , 0, 0, 0, '', 0, 10009, 0, '', 1, 4, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date_type' ,  5, 'Date Type'    , 'Date Type'    , 0, 0, 0, '', 0, 107, 0, '', 1, 5, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'value_type',  6, 'Value Type'  , 'Value Type'  , 0, 0, 0, '', 0, 10010, 0, '', 1, 6, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'value'     ,  7, 'Value'        , 'Value'        , 0, 0, 0, '', 0,   0, 0, '', 1, 7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'value_text',  7, 'Value Text'    , 'Value Text'        , 0, 0, 0, '', 0,   0, 0, '', 1, 7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'   ,  8, 'Log User'    , 'Log User'    , 0, 0, 0, '', 0,   0, 0, '', 0, 99, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'   ,  9, 'Log Time'    , 'Log Time'    , 0, 0, 0, '', 0,   0, 0, '', 0, 99, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1 
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--將欄位次序調整成與 Table Scheme 相同
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_report_control';

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT '更新 app_etl_report_control 結束!'
GO
SET ANSI_PADDING OFF
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_report_set.sql"  
--this script is created by SpecCreator
/*---------------------------------
 版本 : 1
 日期 : 2016-03-14 
 內容 : app_etl_report_set
---------------------------------*/
BEGIN TRANSACTION 

--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_report_set] (
	[id]      	VARCHAR(20) NOT NULL,
	[name]    	VARCHAR(40) NOT NULL,
	[typename]	VARCHAR(50) NOT NULL,
	[dllname] 	VARCHAR(20) NOT NULL,
	[savename]	VARCHAR(200) NOT NULL,
	[itempos] 	VARCHAR(15) NOT NULL,
	[itemid] 	INT NOT NULL,
	[note]    	VARCHAR(200) NOT NULL,
	[loguser] 	VARCHAR(20) NOT NULL,
	[logtime] 	DATETIME NOT NULL	
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_report_set]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_report_set', 'Tmp_app_etl_report_set'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_report_set]') AND type in (N'U'))
	DROP TABLE app_etl_report_set;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_report_set', 'app_etl_report_set', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_report_set] ADD CONSTRAINT [PK_app_etl_report_set] PRIMARY KEY CLUSTERED
(
	[id]
)   
ON [PRIMARY]
GO

--6.完成(買單).....
COMMIT;

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_etl_report_set', 'ALL';

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_etl_report_set', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '報表作業';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'id'      ,  1, 'ID', 'ID', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'    ,  2, 'Name', 'Name', 0, 0, 0, '', 0,   0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'typename',  3, 'Type Name'    , 'Type Name'    , 0, 0, 0, '', 0,   0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'dllname' ,  4, 'Dll Name'     , 'Dll Name'     , 0, 0, 0, '', 0,   0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'savename',  5, 'Save File Name', 'Save File Name', 0, 0, 0, '', 0,   0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'itempos' ,  6, 'Menu Position'    , 'Menu Position'    , 0, 0, 0, '', 0,   0, 0, '', 1, 6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'itemid'  ,  7, 'Menu Parameter'    , 'Menu Parameter'    , 0, 0, 0, '', 0,   0, 0, '', 1, 7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'    ,  8, 'Note'        , 'Note'        , 0, 0, 0, '', 0,   0, 0, '', 1, 8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser' ,  9, 'Log User'    , 'Log User'    , 0, 0, 0, '', 0,   0, 0, '', 0, 99, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime' , 10, 'Log Time'    , 'Log Time'    , 0, 0, 0, '', 0,   0, 0, '', 0, 99, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1 
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--將欄位次序調整成與 Table Scheme 相同
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_report_set';

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT '更新 app_etl_report_set 結束!'
GO
SET ANSI_PADDING OFF
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_set.sql"  
/*---------------------------------
 版本 : 1.0.2
 作者 : Alex
 內容 : 放寬txt檔欄位長度限制至VARCHAR(500)
 日期 : 2015/9/7  
 版本 : 1.0.1
 作者 : Alex
 內容 : 放寬txt檔欄位長度限制至VARCHAR(100)
 日期 : 2014/9/3  
 版本 : 1.0.0
 作者 : Alex
 內容 : app_etl_set
 日期 : 2014/9/3  
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_set] (
	[id]								VARCHAR(20) NOT NULL,
	[name]								VARCHAR(40) NOT NULL,
	[transform_type]					SMALLINT NOT NULL,
	[source_from]						VARCHAR(20) NOT NULL,
	[source_from_table]					VARCHAR(30) NOT NULL,
	[query_command]						VARCHAR(3000) NOT NULL,
	[source_filename]					VARCHAR(255) NOT NULL,
	[usecolumnname]						BIT NOT NULL,
	[headerindex]						INT NOT NULL,
	[source_into]						VARCHAR(20) NOT NULL,
	[source_into_table]					VARCHAR(30) NOT NULL,
	[data_delete_type]					SMALLINT NOT NULL,
	[data_delete_column]				VARCHAR(40) NOT NULL,
	[data_delete_rule]					VARCHAR(300) NOT NULL,
	[assembly_name]						VARCHAR(100) NOT NULL,
	[assembly_type]						VARCHAR(100) NOT NULL,
	[sourcefilter]						VARCHAR(300) NOT NULL,
	[txt_fld_length]					VARCHAR(500) NOT NULL,
	[sp_symbol]							VARCHAR(20) NOT NULL,
	[log_chk]							BIT	NOT NULL,
	[loguser]							VARCHAR(20) NOT NULL,
	[logtime]							DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_set]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_set', 'Tmp_app_etl_set'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_set]') AND type in (N'U'))
	DROP TABLE app_etl_set;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_set', 'app_etl_set', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_set] ADD 
	CONSTRAINT [PK_app_etl_set] PRIMARY KEY  CLUSTERED 
	(
	  [id]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_etl_set', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_etl_set', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'id',					 1, 'ID',		'ID',		0, 0, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name',				 2, 'Name',		'Name',		0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'transform_type',		 3, 'Source Type',		'Source Type',		0, 0, 0, '', 0, 100, 0, '', 1,  3, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source_from',		 4, 'Source',			'Source',			0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source_from_table',	 5, 'Source Table',			'Source Table',			0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'query_command',		 6, 'Command',				'Command',				0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source_filename',	 7, 'Source File Name',			'Source File Name',			0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'usecolumnname',		 8, 'Use Column Name',		'Use Column Name',		0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'headerindex',		 9, 'Header Index',			'Header Index',			0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source_into',		10, 'Target DB',		'Target DB',		0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source_into_table',	11, 'Target Table',		'Target Table',		0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'data_delete_type',	12, 'Duplcated Data Delete Type', 'Duplcated Data Delete Type', 0, 0, 0, '', 0, 102, 0, '', 1, 12, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'data_delete_column', 13, 'Data Delete Column', 'Data Delete Column', 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'data_delete_rule',	14, 'Date Delete Rule',		'Date Delete Rule',		0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'assembly_name',		15, 'Assembly Name',	'Assembly Name',	0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'assembly_type',		16, 'Assembly Type',		'Assembly Type',		0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'sourcefilter',		17, 'Source Filter',		'Source Filter',		0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'txt_fld_length',		18, 'Txt Field Length',	'Txt Field Length',	0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'sp_symbol',			19, 'Txt Separator Symbol',	'Txt Separator Symbol',	0, 0, 0, '', 0,   0, 0, '', 1, 19, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'log_chk',			20, 'Log Check',		'Log Check',		0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser',			21, 'Log User',			'Log User',			0, 0, 0, '', 0,   0, 0, '', 0, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime',			22, 'Log Time',			'Log Time',			0, 0, 0, '', 0,   0, 0, '', 0, 22, 150, 'DateEdit', @loguser, @dt;


IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_set';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 

IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_etl_set 結束!' 
GO 
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_setmap.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2014/9/3
 內容 : app_etl_setmap
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_setmap] (
	[id]				VARCHAR(20) NOT NULL,
	[targetfield]		VARCHAR(40) NOT NULL,
	[sourcefield]		VARCHAR(40) NOT NULL,
	[tranfertype]		SMALLINT NOT NULL,
	[mapcode]			VARCHAR(20) NOT NULL,
	[transferid]		VARCHAR(20) NOT NULL,
	[indx]				SMALLINT NOT NULL,
	[updatetype]		SMALLINT NOT NULL,
	[pkeytype]			SMALLINT NOT NULL,
	[loguser]			VARCHAR(20) NOT NULL,
	[logtime]			DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_setmap]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_setmap', 'Tmp_app_etl_setmap'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_setmap]') AND type in (N'U'))
	DROP TABLE app_etl_setmap;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_setmap', 'app_etl_setmap', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_setmap] ADD 
	CONSTRAINT [PK_app_etl_setmap] PRIMARY KEY  CLUSTERED 
	(
	  [id],
	  [targetfield]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_etl_setmap', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_etl_setmap', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
	SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
	INSERT #appTableField SELECT @tbname, 'id', 1, 'ID', 'ID', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
	INSERT #appTableField SELECT @tbname, 'targetfield', 2, 'Target Field', 'Target Field', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
	INSERT #appTableField SELECT @tbname, 'sourcefield', 3, 'Source Field', 'Source Field', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'LookUpEdit', @loguser, @dt;
	INSERT #appTableField SELECT @tbname, 'tranfertype', 4, 'Transform Type', 'Transform Type', 0, 0, 0, '', 0, 103, 0, '', 1, 5, 150, 'LookUpEdit', @loguser, @dt;
  INSERT #appTableField SELECT @tbname, 'mapcode', 5, 'Map Code', 'Map Code', 0, 0, 0, '', 0, 0, 0, '', 1, 5, 150, 'LookUpEdit', @loguser, @dt;
  INSERT #appTableField SELECT @tbname, 'transferid', 6, 'Tranform ID', 'Tranform ID', 0, 0, 0, '', 0, 0, 0, '', 1, 5, 150, 'LookUpEdit', @loguser, @dt;
  INSERT #appTableField SELECT @tbname, 'indx', 7, 'Index', 'Index', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
	INSERT #appTableField SELECT @tbname, 'updatetype', 8, 'Update Type', 'Update Type', 0, 0, 0, '', 0, 106, 0, '', 1, 5, 150, 'LookUpEdit', @loguser, @dt;
	INSERT #appTableField SELECT @tbname, 'pkeytype', 9, 'Primary Key Type', 'Primary Key Type', 0, 0, 0, '', 0, 108, 0, '', 1, 5, 150, 'LookUpEdit', @loguser, @dt;
	INSERT #appTableField SELECT @tbname, 'loguser', 10, 'Log User', 'Log User', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
	INSERT #appTableField SELECT @tbname, 'logtime', 11, 'Log Time', 'Log Time', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;

	DELETE app_table_field WHERE tablename = @tbname; 
	INSERT app_table_field SELECT * FROM #appTableField; 
	DROP TABLE #appTableField; 
	
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_setmap';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 

IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_etl_setmap 結束!' 
GO 
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_etl_transfer.sql"  
/*---------------------------------
 版本 : 1.0.0
 日期 : 2012/5/31
 內容 : app_etl_transfer(自定義轉換邏輯)
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_etl_transfer] (
	[id]							VARCHAR(20) NOT NULL,
	[name]						VARCHAR(40) NOT NULL,
	[abbr]						VARCHAR(100) NOT NULL,
	[code]						VARCHAR(1000) NOT NULL,
	[assembly_name]		VARCHAR(100) NOT NULL,
	[assembly_type]		VARCHAR(100) NOT NULL,
	[funcname]				VARCHAR(100) NOT NULL,
	[loguser]					VARCHAR(20) NOT NULL,
	[logtime]					DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_transfer]') AND type in (N'U'))
	EXEC sp_backup_data 'app_etl_transfer', 'Tmp_app_etl_transfer'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_etl_transfer]') AND type in (N'U'))
	DROP TABLE app_etl_transfer;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_etl_transfer', 'app_etl_transfer', 'OBJECT'
GO

ALTER TABLE [dbo].[app_etl_transfer] ADD 
	CONSTRAINT [PK_app_etl_transfer] PRIMARY KEY  CLUSTERED 
	(
	  [id]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_etl_transfer', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_etl_transfer', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'id', 1, 'ID', 'ID', 0, 0, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name', 2, 'Name', 'Name', 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'abbr', 3, 'Remark', 'Remark', 0, 0, 0, '', 0, 0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'code', 4, 'Code', 'Code', 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'assembly_name', 5, 'Assembly Name', 'Assembly Name', 0, 0, 0, '', 0, 0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'assembly_type', 6, 'Assembly Type', 'Assembly Type', 0, 0, 0, '', 0, 0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'funcname', 6, 'Function Name', 'Function Name', 0, 0, 0, '', 0, 0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser', 6, 'Log User', 'Log User', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime', 7, 'Log Time', 'Log Time', 0, 0, 0, '', 0, 0, 0, '', 0, 0, 0, '', @loguser, @dt;


IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_etl_transfer';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_etl_transfer 結束!' 
GO 

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_fax_setting.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000270
 日期 : 2017-11-20
 內容 : app_fax_setting
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_fax_setting] (
	[setid]      	VARCHAR(20) NOT NULL,
	[hostname]   	VARCHAR(30) NOT NULL,
	[protocol_type] SMALLINT NOT NULL,
	[credentials]	BIT NOT NULL,	
	[userid]     	VARCHAR(30) NOT NULL,
	[psw]        	VARCHAR(20) NOT NULL,
	[is_psw_fixed]	BIT NOT NULL,
	[loguser]    	VARCHAR(20) NOT NULL,
	[logtime]    	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_fax_setting]') AND type in (N'U'))
	EXEC sp_backup_data 'app_fax_setting', 'Tmp_app_fax_setting'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_fax_setting]') AND type in (N'U'))
	DROP TABLE app_fax_setting;	
	
EXEC sp_rename 'Tmp_app_fax_setting', 'app_fax_setting', 'OBJECT'
GO	

ALTER TABLE [dbo].[app_fax_setting] ADD CONSTRAINT [PK_app_fax_setting] PRIMARY KEY CLUSTERED
(
	[setid]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_fax_setting', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_fax_setting', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Fax Server Setting';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'setid'			,  1, 'ID'					, 'ID'					, 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit'	, @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'hostname'		,  2, 'Host Name'			, 'Host Name'			, 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit'	, @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'protocol_type'   ,  3, 'Port'				, 'Port'				, 0, 0, 0, '', 0, 109, 0, '', 1,  3, 150, 'CalcEdit'	, @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'credentials'		,  4, 'Credentials'			, 'Credentials'			, 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'CheckEdit'	, @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'userid'			,  5, 'ID'					, 'ID'					, 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit'	, @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'psw'				,  6, 'Password'			, 'Password'			, 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit'	, @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_psw_fixed'	,  7, 'Is Password Fixed'   , 'Is Password Fixed'	, 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'CheckEdit'	, @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'			,  8, 'Log User'			, 'Log User'			, 0, 0, 0, '', 0,   0, 0, '', 0,  8, 150, 'TextEdit'	, @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'			,  9, 'Log Time'			, 'Log Time'			, 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'DateEdit'	, @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_fax_setting';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_fax_setting Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_mailsetting.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2014-09-24
 內容 : app_mailsetting
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_mailsetting] (
	[setid]      	VARCHAR(20) NOT NULL,
	[hostname]   	VARCHAR(30) NOT NULL,
	[portnum]    	INT NOT NULL,
	[credentials]	BIT NOT NULL,
	[ssl]        	BIT NOT NULL,
	[userid]     	VARCHAR(30) NOT NULL,
	[psw]        	VARCHAR(20) NOT NULL,
	[loguser]    	VARCHAR(20) NOT NULL,
	[logtime]    	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_mailsetting]') AND type in (N'U'))
	EXEC sp_backup_data 'app_mailsetting', 'Tmp_app_mailsetting'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_mailsetting]') AND type in (N'U'))
	DROP TABLE app_mailsetting;	
	
EXEC sp_rename 'Tmp_app_mailsetting', 'app_mailsetting', 'OBJECT'
GO	

ALTER TABLE [dbo].[app_mailsetting] ADD CONSTRAINT [PK_app_mailsetting] PRIMARY KEY CLUSTERED
(
	[setid]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_mailsetting', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_mailsetting', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'EMail主機設定';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'setid'      ,  1, 'ID'         , 'ID'         , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'hostname'   ,  2, 'Host Name'  , 'Host Name'  , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'portnum'    ,  3, 'Port'       , 'Port'       , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'credentials',  4, 'Credentials', 'Credentials', 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ssl'        ,  5, 'Use SSL'    , 'Use SSL'    , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'userid'     ,  6, 'Email'       , 'Email'       , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'psw'        ,  7, 'Password'       , 'Password'       , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'    ,  8, 'Log User'   , 'Log User'   , 0, 0, 0, '', 0,   0, 0, '', 0,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'    ,  9, 'Log Time'   , 'Log Time'   , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_mailsetting';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_mailsetting Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\app_runer_def.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2014-09-03
 內容 : app_runer_def
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_runer_def] (
	[runid]  	VARCHAR(20) NOT NULL,
	[runname]	VARCHAR(40) NOT NULL,
	[remark] 	VARCHAR(100) NOT NULL,
	[runcode]	VARCHAR(1000) NOT NULL,
	[runtp]  	SMALLINT NOT NULL,
	[loguser]	VARCHAR(20) NOT NULL,
	[logtime]	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_runer_def]') AND type in (N'U'))
	EXEC sp_backup_data 'app_runer_def', 'Tmp_app_runer_def'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_runer_def]') AND type in (N'U'))
	DROP TABLE app_runer_def;	
	
EXEC sp_rename 'Tmp_app_runer_def', 'app_runer_def', 'OBJECT'
GO	

ALTER TABLE [dbo].[app_runer_def] ADD CONSTRAINT [PK_app_runer_def] PRIMARY KEY CLUSTERED
(
	[runid]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_runer_def', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_runer_def', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '執行程序設定';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'runid'  ,  1, 'ID'        , 'ID'        , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'runname',  2, 'Name'        , 'Name'        , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark' ,  3, 'Remark'        , 'Remark'        , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'runcode',  4, 'Code'    , 'Code'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'runtp'  ,  5, 'Type', 'Type', 0, 0, 0, '', 0, 112, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser',  6, 'Log User'    , 'Log User'    , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime',  7, 'Log Time'    , 'Log Time'    , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_runer_def';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_runer_def Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\etl_channel_conf.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2014-09-05
 內容 : etl_channel_conf
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_etl_channel_conf] (
	[id]          	VARCHAR(20) NOT NULL,
	[table_name]  	VARCHAR(40) NOT NULL,
	[channel]     	VARCHAR(2) NOT NULL,
	[source]      	VARCHAR(6) NOT NULL,
	[batchno]     	INT NOT NULL,
	[date_fldname]	VARCHAR(40) NOT NULL,
	[chkno]       	SMALLINT NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[etl_channel_conf]') AND type in (N'U'))
	EXEC sp_backup_data 'etl_channel_conf', 'Tmp_etl_channel_conf'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[etl_channel_conf]') AND type in (N'U'))
	DROP TABLE etl_channel_conf;

EXEC sp_rename 'Tmp_etl_channel_conf', 'etl_channel_conf', 'OBJECT'
GO

ALTER TABLE [dbo].[etl_channel_conf] ADD CONSTRAINT [PK_etl_channel_conf] PRIMARY KEY CLUSTERED
(
	[id]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'etl_channel_conf', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'etl_channel_conf', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '配合系統設定檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'id'          ,  1, '匯入設定代碼', '匯入設定代碼', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'table_name'  ,  2, 'Table名稱'   , 'Table名稱'   , 0, 0, 0, '', 0,   0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'channel'     ,  3, '配合系統'    , '配合系統'    , 0, 0, 0, '', 0,   0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source'      ,  4, '來源類別'    , '來源類別'    , 0, 0, 0, '', 0,   0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'batchno'     ,  5, '批次代號'    , '批次代號'    , 0, 0, 0, '', 0,   0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date_fldname',  6, '時間欄位名稱', '時間欄位名稱', 0, 0, 0, '', 0,   0, 0, '', 1, 6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'chkno'       ,  7, '檢查代碼'    , '檢查代碼'    , 0, 0, 0, '', 0, 120, 0,'1', 1, 7, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  8, '異動人員'    , '異動人員'    , 0, 0, 0, '', 0,   0, 0, '', 1, 8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     ,  9, '異動時間'    , '異動時間'    , 0, 0, 0, '', 0,   0, 0, '', 1, 9, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'etl_channel_conf';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table etl_channel_conf Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\ETL\etl_transfer_rpt.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000270
 日期 : 2014-09-03
 內容 : etl_transfer_rpt
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_etl_transfer_rpt] (
	[channel]   	VARCHAR(2) NOT NULL,
	[source]    	VARCHAR(6) NOT NULL,
	[table_name]	VARCHAR(40) NOT NULL,
	[batchno]   	INT NOT NULL,
	[date]      	SMALLDATETIME NOT NULL,
	[datacount] 	INT NOT NULL,
	[rctime]    	DATETIME NOT NULL,
	[transcount]	INT NOT NULL,
	[tstime]    	DATETIME NOT NULL,
	[suss]      	BIT NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[etl_transfer_rpt]') AND type in (N'U'))
	EXEC sp_backup_data 'etl_transfer_rpt', 'Tmp_etl_transfer_rpt'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[etl_transfer_rpt]') AND type in (N'U'))
	DROP TABLE etl_transfer_rpt;

EXEC sp_rename 'Tmp_etl_transfer_rpt', 'etl_transfer_rpt', 'OBJECT'
GO

ALTER TABLE [dbo].[etl_transfer_rpt] ADD CONSTRAINT [PK_etl_transfer_rpt] PRIMARY KEY CLUSTERED
(
	[channel],[source],[table_name],[batchno],[date]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'etl_transfer_rpt', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'etl_transfer_rpt', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '轉檔結果檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'channel'   ,  1, '配合系統'    , '配合系統'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source'    ,  2, '來源類別'    , '來源類別'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'table_name',  3, 'Table名稱'   , 'Table名稱'   , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'batchno'   ,  4, '批次代號'    , '批次代號'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date'      ,  5, '資料日期'    , '資料日期'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'datacount' ,  6, '來源資料筆數', '來源資料筆數', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rctime'    ,  7, '寫入時間'    , '寫入時間'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'transcount',  8, '轉入筆數'    , '轉入筆數'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tstime'    ,  9, '轉入時間'    , '轉入時間'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'suss'      , 10, '轉檔成功'    , '轉檔成功'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'etl_transfer_rpt';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table etl_transfer_rpt Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???T?{\cfm_confirmed_record.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-11-13
 內容 : cfm_confirmed_record
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cfm_confirmed_record] (
	[seq]                    	INT NOT NULL,
	[cfm_received_record_seq]	INT NOT NULL,
	[trade_no]               	VARCHAR(13) NOT NULL,
	[cfm_type]               	SMALLINT NOT NULL,
	[remark]                 	NVARCHAR(100) NOT NULL,
	[loguser]                	VARCHAR(20) NOT NULL,
	[logtime]                	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_confirmed_record]') AND type in (N'U'))
	EXEC sp_backup_data 'cfm_confirmed_record', 'Tmp_cfm_confirmed_record'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_confirmed_record]') AND type in (N'U'))
	DROP TABLE cfm_confirmed_record;

EXEC sp_rename 'Tmp_cfm_confirmed_record', 'cfm_confirmed_record', 'OBJECT'
GO

ALTER TABLE [dbo].[cfm_confirmed_record] ADD CONSTRAINT [PK_cfm_confirmed_record] PRIMARY KEY CLUSTERED
(
    [seq]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cfm_confirmed_record', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cfm_confirmed_record', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'seq'                    ,  1, ''              , ''              , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_received_record_seq',  2, 'Received Seq'  , 'Received Seq'  , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_no'               ,  2, 'Deal Number'   , 'Deal Number'   , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_type'               ,  2, 'Confirmed Type', 'Confirmed Type', 0, 0, 0, '', 0, 516, 0, '', 1,  2, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark'                 ,  4, 'Remark'        , 'Remark'        , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'                ,  5, 'Loguser'       , 'Loguser'       , 0, 0, 0, '', 0,   0, 0, '', 0,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'                ,  6, 'Logtime'       , 'Logtime'       , 0, 0, 0, '', 0,   0, 0, '', 0,  6, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cfm_confirmed_record';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cfm_confirmed_record Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???T?{\cfm_delivered_record_fx.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-11-09
 內容 : cfm_delivered_record_fx
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cfm_delivered_record_fx] (
	[seq]          	INT NOT NULL,
	[trade_no]     	VARCHAR(13) NOT NULL,
	[delivered_type]	SMALLINT NOT NULL,
	[file_name]    	NVARCHAR(50) NOT NULL,
	[status]       	SMALLINT NOT NULL,
	[form_type]    	SMALLINT NOT NULL,
	[param]        	VARCHAR(100) NOT NULL,
	[remark]       	NVARCHAR(500) NOT NULL,
	[loguser]      	VARCHAR(20) NOT NULL,
	[logtime]      	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_delivered_record_fx]') AND type in (N'U'))
	EXEC sp_backup_data 'cfm_delivered_record_fx', 'Tmp_cfm_delivered_record_fx'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_delivered_record_fx]') AND type in (N'U'))
	DROP TABLE cfm_delivered_record_fx;

EXEC sp_rename 'Tmp_cfm_delivered_record_fx', 'cfm_delivered_record_fx', 'OBJECT'
GO

ALTER TABLE [dbo].[cfm_delivered_record_fx] ADD CONSTRAINT [PK_cfm_delivered_record_fx] PRIMARY KEY CLUSTERED
(
    [seq],[trade_no]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cfm_delivered_record_fx', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cfm_delivered_record_fx', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'seq'          ,  1, 'Sequence'     , 'Sequence'     , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_no'     ,  2, 'Deal Number'  , 'Deal Number'  , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'delivered_type', 3, 'Delivered Type','Delivered Type', 0, 0, 0, '', 0, 508, 0, '', 1,  3, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_name'    ,  4, 'File Name'    , 'File Name'    , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'status'       ,  5, 'Status'       , 'Status'       , 0, 0, 0, '', 0, 515, 0, '', 1,  5, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'form_type'    ,  6, 'Form Type'    , 'Form Type'    , 0, 0, 0, '', 0,  -1, 0, '', 1,  6, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'param'        ,  7, 'parameter'    , 'parameter'    , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark'       ,  8, 'Remark'       , 'Remark'       , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'      ,  9, 'Loguser'      , 'Loguser'      , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'      , 10, 'Logtime'      , 'Logtime'      , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cfm_delivered_record_fx';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cfm_delivered_record_fx Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???T?{\cfm_email_format.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-10-31
 內容 : cfm_email_format
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cfm_email_format] (
	[cfm_type]         	SMALLINT NOT NULL,
	[desc]             	NVARCHAR(500) NOT NULL,
	[subject]          	NVARCHAR(500) NOT NULL,
	[body]             	NVARCHAR(1000) NOT NULL,
	[carbon_copy]      	VARCHAR(500) NOT NULL,
	[blind_carbon_copy]	VARCHAR(500) NOT NULL,
	[logusr]           	VARCHAR(20) NOT NULL,
	[logtime]          	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_email_format]') AND type in (N'U'))
	EXEC sp_backup_data 'cfm_email_format', 'Tmp_cfm_email_format'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_email_format]') AND type in (N'U'))
	DROP TABLE cfm_email_format;	
	
EXEC sp_rename 'Tmp_cfm_email_format', 'cfm_email_format', 'OBJECT'
GO	

ALTER TABLE [dbo].[cfm_email_format] ADD CONSTRAINT [PK_cfm_email_format] PRIMARY KEY CLUSTERED
(
	[cfm_type]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cfm_email_format', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cfm_email_format', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Confirmation Email Format';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'cfm_type'         ,  1, 'Confirmation Type', 'Confirmation Type', 1, 1, 0, '', 0, 114, 0, '', 1,  1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'desc'             ,  2, 'Description'      , 'Description'      , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'subject'          ,  3, 'Subject'          , 'Subject'          , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'body'             ,  4, 'Body'             , 'Body'             , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'carbon_copy'      ,  5, 'Carbon Copy'      , 'Carbon Copy'      , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'blind_carbon_copy',  6, 'Blind Carbon Copy', 'Blind Carbon Copy', 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logusr'           ,  7, 'Loguser'          , 'Loguser'          , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'          ,  8, 'Logtime'          , 'Logtime'          , 0, 0, 0, '', 0,   0, 0, '', 0,  8, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cfm_email_format';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cfm_email_format Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???T?{\cfm_received_record.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-11-09
 內容 : cfm_received_record
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cfm_received_record] (
	[seq]         	INT NOT NULL,
	[trade_no]    	VARCHAR(13) NOT NULL,
	[receive_time]	DATETIME NOT NULL,
	[receive_type]	SMALLINT NOT NULL,
	[cfm_status]  	SMALLINT NOT NULL,
	[file_name]   	NVARCHAR(500) NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_received_record]') AND type in (N'U'))
	EXEC sp_backup_data 'cfm_received_record', 'Tmp_cfm_received_record'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_received_record]') AND type in (N'U'))
	DROP TABLE cfm_received_record;

EXEC sp_rename 'Tmp_cfm_received_record', 'cfm_received_record', 'OBJECT'
GO

ALTER TABLE [dbo].[cfm_received_record] ADD CONSTRAINT [PK_cfm_received_record] PRIMARY KEY CLUSTERED
(
    [seq]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cfm_received_record', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cfm_received_record', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '已收之交易通知書';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'seq'         ,  1, 'Sequence'           , 'Sequence'           , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_no'    ,  2, 'Deal Number'        , 'Deal Number'        , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'receive_time',  3, 'Received Time'      , 'Received Time'      , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'receive_type',  4, 'Received Type'      , 'Received Type'      , 0, 0, 0, '', 0,  -1, 0, '', 1,  4, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_status'  ,  5, 'Confirmation Status', 'Confirmation Status', 0, 0, 0, '', 0, 514, 0, '', 1,  5, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_name'   ,  6, 'File Name'          , 'File Name'          , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  7, 'Loguser'            , 'Loguser'            , 0, 0, 0, '', 0,   0, 0, '', 0,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     ,  8, 'Logtime'            , 'Logtime'            , 0, 0, 0, '', 0,   0, 0, '', 0,  8, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cfm_received_record';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cfm_received_record Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???T?{\cfm_static_data.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-10-31
 內容 : cfm_static_data
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cfm_static_data] (
	[cfm_type]   	SMALLINT NOT NULL,
	[static_data]	NVARCHAR(1000) NOT NULL,
	[loguser]    	VARCHAR(20) NOT NULL,
	[logtime]    	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_static_data]') AND type in (N'U'))
	EXEC sp_backup_data 'cfm_static_data', 'Tmp_cfm_static_data'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cfm_static_data]') AND type in (N'U'))
	DROP TABLE cfm_static_data;

EXEC sp_rename 'Tmp_cfm_static_data', 'cfm_static_data', 'OBJECT'
GO

ALTER TABLE [dbo].[cfm_static_data] ADD CONSTRAINT [PK_cfm_static_data] PRIMARY KEY CLUSTERED
(
    [cfm_type]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cfm_static_data', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cfm_static_data', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'CFM Static Data';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'cfm_type'   ,  1, 'Confirmation Type', 'Confirmation Type', 1, 1, 0, '', 0,  -1, 0, '', 1,  1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'static_data',  2, 'Static Data'      , 'Static Data'      , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'    ,  3, 'Loguser'          , 'Loguser'          , 0, 0, 0, '', 0,   0, 0, '', 0,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'    ,  4, 'Logtime'          , 'Logtime'          , 0, 0, 0, '', 0,   0, 0, '', 0,  4, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cfm_static_data';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cfm_static_data Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???P?w?s\FX\tra_fx.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-11-20
 內容 : tra_fx
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_tra_fx] (
	[trade_no]         	VARCHAR(13) NOT NULL,
	[wss_tid]          	VARCHAR(15) NOT NULL,
	[orig_wss_tid]     	VARCHAR(15) NOT NULL,
	[trade_date]       	DATE NOT NULL,
	[value_date]       	DATE NOT NULL,
	[cust_tid]         	VARCHAR(15) NOT NULL,
	[pno]              	INT NOT NULL,
	[deal_code]        	VARCHAR(2) NOT NULL,
	[trade_type]       	SMALLINT NOT NULL,
        [ccy_main]              CHAR(3) NOT NULL,
	[ccy_buy]          	CHAR(3) NOT NULL,
	[amt_buy]          	NUMERIC(20,5) NOT NULL,
	[ccy_sell]         	CHAR(3) NOT NULL,
	[amt_sell]         	NUMERIC(20,5) NOT NULL,
	[base_equiv_amt]   	NUMERIC(20,5) NOT NULL,
	[rate]             	NUMERIC(20,10) NOT NULL,
	[base_ccy]         	VARCHAR(8) NOT NULL,
	[orig_ndf_tid]     	VARCHAR(15) NOT NULL,
	[ndf_stl_ccy]      	CHAR(3) NOT NULL,
	[ndf_fix_date]     	DATE NOT NULL,
	[swap_tid]         	VARCHAR(15) NOT NULL,
	[swap_sf]          	SMALLINT NOT NULL,
	[swap_point]       	NUMERIC(20,5) NOT NULL,
	[orig_product_type]	SMALLINT NOT NULL,
	[product_type]     	SMALLINT NOT NULL,
	[ref_no]           	VARCHAR(15) NOT NULL,
	[orig_ref_no]      	VARCHAR(15) NOT NULL,
	[status]           	VARCHAR(3) NOT NULL,
	[cancel_reason]    	VARCHAR(30) NOT NULL,
	[cancel_date]      	DATE NOT NULL,
	[broker_type]      	SMALLINT NOT NULL,
	[is_settled]       	BIT NOT NULL,
	[imm_pay]          	BIT NOT NULL,
	[imm_confirm]      	BIT NOT NULL,
	[is_non_std_ndf]   	BIT NOT NULL,
	[non_std_comment]  	VARCHAR(100) NOT NULL,
	[delivery_comment] 	NVARCHAR(100) NOT NULL,
	[remark1]          	VARCHAR(30) NOT NULL,
	[remark2]          	VARCHAR(30) NOT NULL,
	[remark3]          	VARCHAR(30) NOT NULL,
	[pay_nostro]         	VARCHAR(10) NOT NULL,
	[trader]           	VARCHAR(3) NOT NULL,
	[trader_name]      	VARCHAR(20) NOT NULL,
	[entry_dateime]    	DATE NOT NULL,
	[fsi_tid]          	VARCHAR(15) NOT NULL,
	[fsi_rec_tid]      	VARCHAR(15) NOT NULL,
	[loguser]          	VARCHAR(20) NOT NULL,
	[logtime]          	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_fx]') AND type in (N'U'))
	EXEC sp_backup_data 'tra_fx', 'Tmp_tra_fx'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_fx]') AND type in (N'U'))
	DROP TABLE tra_fx;

EXEC sp_rename 'Tmp_tra_fx', 'tra_fx', 'OBJECT'
GO

ALTER TABLE [dbo].[tra_fx] ADD CONSTRAINT [PK_tra_fx] PRIMARY KEY CLUSTERED
(
    [trade_no]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'tra_fx', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'tra_fx', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '外匯交易';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'trade_no'         ,1, 'Deal Number'             , 'Deal Number'             ,1,1,0, '',0,0,0, '',1,1,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'wss_tid'          ,2, 'WSS TID'                 , 'WSS TID'                 ,0,0,0, '',0,0,0, '',1,2,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'orig_wss_tid'     ,3, 'Orig WSS TID'            , 'Orig WSS TID'            ,0,0,0, '',0,0,0, '',1,3,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_date'       ,4, 'Trade Date'              , 'Trade Date'              ,0,0,0, '',0,0,0, '',1,4,150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'value_date'       ,5, 'Value Date'              , 'Value Date'              ,0,0,0, '',0,0,0, '',1,5,150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cust_tid'         ,6, 'Customer Tid'            , 'Customer Tid'            ,0,0,0, '',0,0,0, '',1,6,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'pno'              ,7, '客戶代碼'                , '客戶代碼'                ,0,0,0, '',0,0,0, '',1,7,150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'deal_code'        ,8, 'Deal Code'               , 'Deal Code'               ,0,0,0, '',0,0,0, '',1,8,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_type'       ,9, 'Trade Type'              , 'Trade Type'              ,0,0,0, '',0,2,0, '',1,9,150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy_main'         ,10, 'Main Ccy'                , 'Main Ccy'                ,0,0,0, '',0,0,0, '',1,10,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy_buy'          ,11, 'Ccy Bought'              , 'Ccy Bought'              ,0,0,0, '',0,0,0, '',1,11,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'amt_buy'          ,12, 'Amount Bought'           , 'Amount Bought'           ,0,0,0, '',0,0,0, '',1,12,150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy_sell'         ,13, 'Ccy Sold'                , 'Ccy Sold'                ,0,0,0, '',0,0,0, '',1,13,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'amt_sell'         ,14, 'Amount Sold'             , 'Amount Sold'             ,0,0,0, '',0,0,0, '',1,14,150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'base_equiv_amt'   ,15, 'Base Equiv Amount'       , 'Base Equiv Amount'       ,0,0,0, '',0,0,0, '',1,15,150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rate'             ,16, 'Rate'                    , 'Rate'                    ,0,0,0, '',0,0,0, '',1,16,150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'base_ccy'         ,17, 'Base Ccy'                , 'Base Ccy'                ,0,0,0, '',0,0,0, '',1,17,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'orig_ndf_tid'     ,18, 'Orig NDF TID'            , 'Orig NDF TID'            ,0,0,0, '',0,0,0, '',1,18,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ndf_stl_ccy'      ,19, 'NDF Settle Ccy'          , 'NDF Settle Ccy'          ,0,0,0, '',0,0,0, '',1,19,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ndf_fix_date'     ,20, 'NDF Fixing Date'         , 'NDF Fixing Date'         ,0,0,0, '',0,0,0, '',1,20,150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'swap_tid'         ,21, 'SWAP TID'                , 'SWAP TID'                ,0,0,0, '',0,0,0, '',1,21,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'swap_sf'          ,22, 'SWAP S/F'                , 'SWAP S/F'                ,0,0,0, '',0,75,0, '',1,22,150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'swap_point'       ,23, 'SWAP Point'              , 'SWAP Point'              ,0,0,0, '',0,0,0, '',1,23,150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'orig_product_type',24, 'Orig Product'            , 'Orig Product'            ,0,0,0, '',0,73,0, '',1,24,150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'product_type'     ,25, 'Product'                 , 'Product'                 ,0,0,0, '',0,73,0, '',1,25,150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ref_no'           ,26, 'Ref No.'                 , 'Ref No.'                 ,0,0,0, '',0,0,0, '',1,26,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'orig_ref_no'      ,27, 'Orig Ref No'             , 'Orig Ref No'             ,0,0,0, '',0,0,0, '',1,27,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'status'           ,28, 'Status'                  , 'Status'                  ,0,0,0, '',0,0,0, '',1,28,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cancel_reason'    ,29, 'Cancel Reason'           , 'Cancel Reason'           ,0,0,0, '',0,0,0, '',1,29,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cancel_date'      ,30, 'Cancel Date'             , 'Cancel Date'             ,0,0,0, '',0,0,0, '',1,30,150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'broker_type'      ,31, 'Broker Code'             , 'Broker Code'             ,0,0,0, '',0,7,0, '',1,31,150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_settled'       ,32, 'Is Settled'              , 'Is Settled'              ,0,0,0, '',0,0,0, '',1,32,150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'imm_pay'          ,33, 'Immediately Payment'     , 'Immediately Payment'     ,0,0,0, '',0,0,0, '',1,33,150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'imm_confirm'      ,34, 'Immediately Confirmation', 'Immediately Confirmation',0,0,0, '',0,0,0, '',1,34,150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_non_std_ndf'   ,35, 'Non Standard NDF LF'     , 'Non Standard NDF LF'     ,0,0,0, '',0,0,0, '',1,35,150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'non_std_comment'  ,36, 'Non Standard Fixing Time', 'Non Standard Fixing Time',0,0,0, '',0,0,0, '',1,36,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'delivery_comment' ,37, 'Header Comment'          , 'Header Comment'          ,0,0,0, '',0,0,0, '',1,37,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark1'          ,38, 'Remark1'                 , 'Remark1'                 ,0,0,0, '',0,0,0, '',1,38,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark2'          ,39, 'Remark2'                 , 'Remark2'                 ,0,0,0, '',0,0,0, '',1,39,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark3'          ,40, 'Remark3'                 , 'Remark3'                 ,0,0,0, '',0,0,0, '',1,40,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'pay_nostro'       ,41, 'Pay Nostro'              , 'Pay Nostro'              ,0,0,0, '',0,0,0, '',1,41,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trader'           ,42, 'Trader'                  , 'Trader'                  ,0,0,0, '',0,0,0, '',1,42,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trader_name'      ,43, 'Trader Name'             , 'Trader Name'             ,0,0,0, '',0,0,0, '',1,43,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'entry_dateime'    ,44, 'Enter Date Time'         , 'Enter Date Time'         ,0,0,0, '',0,0,0, '',1,44,150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fsi_tid'          ,45, 'FSI Tid'                 , 'FSI Tid'                 ,0,0,0, '',0,0,0, '',1,45,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fsi_rec_tid'      ,46, 'FSI Rec Tid'             , 'FSI Rec Tid'             ,0,0,0, '',0,0,0, '',1,46,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'          ,47, 'Loguser'                 , 'Loguser'                 ,0,0,0, '',0,0,0, '',0,47,150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'          ,48, 'Logtime'                 , 'Logtime'                 ,0,0,0, '',0,0,0, '',0,48,150, 'DateEdit', @loguser, @dt;


IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'tra_fx';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table tra_fx Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???P?w?s\FX\tra_fx_cfm.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-10-16
 內容 : tra_fx_cfm
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_tra_fx_cfm] (
    [cust_tid]            VARCHAR(15) NOT NULL,
    [pno]                 INT NOT NULL,
    [fx_match_pri]        BIT NOT NULL,
    [fx_match_sec]        BIT NOT NULL,
    [fx_match_swift_1]    VARCHAR(30) NOT NULL,
    [fx_match_swift_2]    VARCHAR(30) NOT NULL,
    [fx_match_swift_3]    VARCHAR(30) NOT NULL,
    [fx_match_swift_4]    VARCHAR(30) NOT NULL,
    [fx_match_swift_5]    VARCHAR(30) NOT NULL,
    [last_action]         VARCHAR(1) NOT NULL,
    [tag_83_swift_1]      VARCHAR(30) NOT NULL,
    [tag_83_swift_2]      VARCHAR(30) NOT NULL,
    [tag_83_swift_3]      VARCHAR(30) NOT NULL,
    [tag_83_swift_4]      VARCHAR(30) NOT NULL,
    [tag_83_swift_5]      VARCHAR(30) NOT NULL,
    [loguser]             VARCHAR(20) NOT NULL,
    [logtime]             DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_fx_cfm]') AND type in (N'U'))
    EXEC sp_backup_data 'tra_fx_cfm', 'Tmp_tra_fx_cfm'
    
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_fx_cfm]') AND type in (N'U'))
    DROP TABLE tra_fx_cfm;    
    
EXEC sp_rename 'Tmp_tra_fx_cfm', 'tra_fx_cfm', 'OBJECT'
GO    

ALTER TABLE [dbo].[tra_fx_cfm] ADD CONSTRAINT [PK_tra_fx_cfm] PRIMARY KEY CLUSTERED
(
    [cust_tid]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'tra_fx_cfm', 'ALL';
    
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'tra_fx_cfm', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'fx交易確認資訊';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'pno'             ,  1, '客戶代碼'             , '客戶代碼'             , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cust_tid'        ,  2, '客戶'                 , '客戶'                 , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fx_match_pri'    ,  3, 'FX Match Primary'     , 'FX Match Primary'     , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fx_match_sec'    ,  4, 'FX Match Secondary'   , 'FX Match Secondary'   , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fx_match_swift_1',  5, 'FX Match SWIFT Line 1', 'FX Match SWIFT Line 1', 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fx_match_swift_2',  6, 'FX Match SWIFT Line 2', 'FX Match SWIFT Line 2', 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fx_match_swift_3',  7, 'FX Match SWIFT Line 3', 'FX Match SWIFT Line 3', 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fx_match_swift_4',  8, 'FX Match SWIFT Line 4', 'FX Match SWIFT Line 4', 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fx_match_swift_5',  9, 'FX Match SWIFT Line 5', 'FX Match SWIFT Line 5', 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'last_action'     , 10, 'Last Action'          , 'Last Action'          , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tag_83_swift_1'  , 11, 'TAG 83 SWIFT Line 1'  , 'TAG 83 SWIFT Line 1'  , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tag_83_swift_2'  , 12, 'TAG 83 SWIFT Line 2'  , 'TAG 83 SWIFT Line 2'  , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tag_83_swift_3'  , 13, 'TAG 83 SWIFT Line 3'  , 'TAG 83 SWIFT Line 3'  , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tag_83_swift_4'  , 14, 'TAG 83 SWIFT Line 4'  , 'TAG 83 SWIFT Line 4'  , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tag_83_swift_5'  , 15, 'TAG 83 SWIFT Line 5'  , 'TAG 83 SWIFT Line 5'  , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'         , 16, 'Loguser'              , 'Loguser'              , 0, 0, 0, '', 0,   0, 0, '', 0, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'         , 17, 'Logtime'              , 'Logtime'              , 0, 0, 0, '', 0,   0, 0, '', 0, 17, 150, 'TextEdit', @loguser, @dt;
    

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'tra_fx_cfm';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table tra_fx_cfm Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???P?w?s\FX\tra_fx_si.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-10-16
 內容 : tra_fx_si
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_tra_fx_si] (
    [wss_tid]        VARCHAR(15) NOT NULL,
    [pno]            INT NOT NULL,
    [cust_tid]       VARCHAR(15) NOT NULL,
    [pay_meth]       VARCHAR(10) NOT NULL,
    [rec_meth]       VARCHAR(10) NOT NULL,
    [rec_nostro]     VARCHAR(8) NOT NULL,
    [ben1]           VARCHAR(30) NOT NULL,
    [ben2]           VARCHAR(30) NOT NULL,
    [ben3]           VARCHAR(30) NOT NULL,
    [ben4]           VARCHAR(30) NOT NULL,
    [ben5]           VARCHAR(30) NOT NULL,
    [acc1]           VARCHAR(30) NOT NULL,
    [acc2]           VARCHAR(30) NOT NULL,
    [acc3]           VARCHAR(30) NOT NULL,
    [acc4]           VARCHAR(30) NOT NULL,
    [acc5]           VARCHAR(30) NOT NULL,
    [add1]           VARCHAR(30) NOT NULL,
    [add1b]          VARCHAR(5) NOT NULL,
    [add2]           VARCHAR(30) NOT NULL,
    [add2b]          VARCHAR(5) NOT NULL,
    [add3]           VARCHAR(30) NOT NULL,
    [add3b]          VARCHAR(5) NOT NULL,
    [add4]           VARCHAR(30) NOT NULL,
    [add4b]          VARCHAR(5) NOT NULL,
    [add5]           VARCHAR(30) NOT NULL,
    [add5b]          VARCHAR(5) NOT NULL,
    [add6]           VARCHAR(30) NOT NULL,
    [add6b]          VARCHAR(5) NOT NULL,
    [inter1]         VARCHAR(35) NOT NULL,
    [inter2]         VARCHAR(35) NOT NULL,
    [inter3]         VARCHAR(35) NOT NULL,
    [inter4]         VARCHAR(35) NOT NULL,
    [inter5]         VARCHAR(35) NOT NULL,
    [city_int_no]    VARCHAR(4) NOT NULL,
    [fsi_id]         VARCHAR(15) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_fx_si]') AND type in (N'U'))
    EXEC sp_backup_data 'tra_fx_si', 'Tmp_tra_fx_si'
    
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_fx_si]') AND type in (N'U'))
    DROP TABLE tra_fx_si;    
    
EXEC sp_rename 'Tmp_tra_fx_si', 'tra_fx_si', 'OBJECT'
GO    

ALTER TABLE [dbo].[tra_fx_si] ADD CONSTRAINT [PK_tra_fx_si] PRIMARY KEY CLUSTERED
(
    [wss_tid]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'tra_fx_si', 'ALL';
    
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'tra_fx_si', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'fx交易確認資訊';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'wss_tid'    ,  1, 'SI Tid'        , 'SI Tid'        , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'pno'        ,  2, '客戶代碼'      , '客戶代碼'      , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cust_tid'   ,  3, 'Customer Tid'  , 'Customer Tid'  , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'pay_meth'   ,  4, 'Pay Meth'      , 'Pay Meth'      , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rec_meth'   ,  5, 'Rec Meth'      , 'Rec Meth'      , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rec_nostro' ,  6, 'Rec Nostro'    , 'Rec Nostro'    , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ben1'       ,  7, 'Ben1'          , 'Ben1'          , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ben2'       ,  8, 'Ben2'          , 'Ben2'          , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ben3'       ,  9, 'Ben3'          , 'Ben3'          , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ben4'       , 10, 'Ben4'          , 'Ben4'          , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ben5'       , 11, 'Ben5'          , 'Ben5'          , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc1'       , 12, 'Acc1'          , 'Acc1'          , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc2'       , 13, 'Acc2'          , 'Acc2'          , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc3'       , 14, 'Acc3'          , 'Acc3'          , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc4'       , 15, 'Acc4'          , 'Acc4'          , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc5'       , 16, 'Acc5'          , 'Acc5'          , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add1'       , 17, 'Add1'          , 'Add1'          , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add1b'      , 18, 'Add1B'         , 'Add1B'         , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add2'       , 19, 'Add2'          , 'Add2'          , 0, 0, 0, '', 0,   0, 0, '', 1, 19, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add2b'      , 20, 'Add2B'         , 'Add2B'         , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add3'       , 21, 'Add3'          , 'Add3'          , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add3b'      , 22, 'Add3B'         , 'Add3B'         , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add4'       , 23, 'Add4'          , 'Add4'          , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add4b'      , 24, 'Add4B'         , 'Add4B'         , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add5'       , 25, 'Add5'          , 'Add5'          , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add5b'      , 26, 'Add5b'         , 'Add5b'         , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add6'       , 27, 'Add6'          , 'Add6'          , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'add6b'      , 28, 'Add6b'         , 'Add6b'         , 0, 0, 0, '', 0,   0, 0, '', 1, 28, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'inter1'     , 29, 'Inter1'        , 'Inter1'        , 0, 0, 0, '', 0,   0, 0, '', 1, 29, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'inter2'     , 30, 'Inter2'        , 'Inter2'        , 0, 0, 0, '', 0,   0, 0, '', 1, 30, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'inter3'     , 31, 'Inter3'        , 'Inter3'        , 0, 0, 0, '', 0,   0, 0, '', 1, 31, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'inter4'     , 32, 'Inter4'        , 'Inter4'        , 0, 0, 0, '', 0,   0, 0, '', 1, 32, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'inter5'     , 33, 'Inter5'        , 'Inter5'        , 0, 0, 0, '', 0,   0, 0, '', 1, 33, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'city_int_no', 34, 'City Int No'   , 'City Int No'   , 0, 0, 0, '', 0,   0, 0, '', 1, 34, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fsi_id'     , 35, 'Fsi Identifier', 'Fsi Identifier', 0, 0, 0, '', 0,   0, 0, '', 1, 35, 150, 'TextEdit', @loguser, @dt;
    

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'tra_fx_si';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table tra_fx_si Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???P?w?s\FX\tra_mm.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-07
 內容 : tra_mm
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_tra_mm] (
	[trade_no]       	VARCHAR(13) NOT NULL,
	[wss_tid]        	VARCHAR(15) NOT NULL,
	[orig_trade_no]  	VARCHAR(13) NOT NULL,
	[orig_wss_tid]   	VARCHAR(15) NOT NULL,
	[trade_date]     	DATE NOT NULL,
	[type]           	SMALLINT NOT NULL,
	[start_date]     	DATE NOT NULL,
	[mat_date]       	DATE NOT NULL,
	[cust_tid]       	VARCHAR(15) NOT NULL,
	[pno]            	INT NOT NULL,
	[ccy]            	CHAR(3) NOT NULL,
	[prod_type]      	SMALLINT NOT NULL,
	[not_amt]        	NUMERIC(20,5) NOT NULL,
	[int_rate]       	NUMERIC(20,5) NOT NULL,
	[price]          	NUMERIC(20,5) NOT NULL,
	[dur]            	VARCHAR(11) NOT NULL,
	[val_at_mat]     	NUMERIC(20,5) NOT NULL,
	[int]            	NUMERIC(20,5) NOT NULL,
	[basis]          	VARCHAR(6) NOT NULL,
	[status]         	VARCHAR(2) NOT NULL,
	[base_ccy]       	VARCHAR(8) NOT NULL,
	[base_equiv_rate]	NUMERIC(20,5) NOT NULL,
	[entry_time]     	DATE NOT NULL,
	[reason]         	VARCHAR(30) NOT NULL,
	[is_confirmed]   	BIT NOT NULL,
	[cfm_time]       	DATETIME NOT NULL,
	[cfm_user]       	VARCHAR(20) NOT NULL,
	[is_cfm_sent]    	BIT NOT NULL,
	[sent_time]      	DATETIME NOT NULL,
	[sent_user]      	VARCHAR(20) NOT NULL,
	[loguser]        	VARCHAR(20) NOT NULL,
	[logtime]        	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_mm]') AND type in (N'U'))
	EXEC sp_backup_data 'tra_mm', 'Tmp_tra_mm'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_mm]') AND type in (N'U'))
	DROP TABLE tra_mm;	
	
EXEC sp_rename 'Tmp_tra_mm', 'tra_mm', 'OBJECT'
GO	

ALTER TABLE [dbo].[tra_mm] ADD CONSTRAINT [PK_tra_mm] PRIMARY KEY CLUSTERED
(
	[trade_no]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'tra_mm', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'tra_mm', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '銀行間調度款';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'trade_no'       ,  1, 'Deal Number'         , 'Deal Number'         , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'wss_tid'        ,  2, 'WSS TID'             , 'WSS TID'             , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'orig_trade_no'  ,  3, 'Orig Deal Number'    , 'Orig Deal Number'    , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'orig_wss_tid'   ,  4, 'Orig TID'            , 'Orig TID'            , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_date'     ,  5, 'Trade Date'          , 'Trade Date'          , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'type'           ,  6, 'Asset Or Liablity'   , 'Asset Or Liablity'   , 0, 0, 0, '', 0,   3, 0, '', 1,  6, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'start_date'     ,  7, 'Start Date'          , 'Start Date'          , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'mat_date'       ,  8, 'Maturity Date'       , 'Maturity Date'       , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cust_tid'       ,  9, 'WSS No.'             , 'WSS No.'             , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'pno'            , 10, '客戶代碼'            , '客戶代碼'            , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy'            , 11, 'Currency'            , 'Currency'            , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'prod_type'      , 12, 'Product'             , 'Product'             , 0, 0, 0, '', 0,   5, 0, '', 1, 12, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'not_amt'        , 13, 'Notional Amount'     , 'Notional Amount'     , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'int_rate'       , 14, 'Interest Rate'       , 'Interest Rate'       , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'price'          , 15, 'Price'               , 'Price'               , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'dur'            , 16, 'Duration'            , 'Duration'            , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'val_at_mat'     , 17, 'Value At Maturity'   , 'Value At Maturity'   , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'int'            , 18, 'Interest'            , 'Interest'            , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'basis'          , 19, 'Basis'               , 'Basis'               , 0, 0, 0, '', 0,   0, 0, '', 1, 19, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'status'         , 20, 'Status'              , 'Status'              , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'base_ccy'       , 21, 'Base CCY'            , 'Base CCY'            , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'base_equiv_rate', 22, 'Base Equiv Rate'     , 'Base Equiv Rate'     , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'entry_time'     , 23, 'Entry Date Time'     , 'Entry Date Time'     , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'reason'         , 24, 'Reason'              , 'Reason'              , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_confirmed'   , 25, 'Is Confirmed'        , 'Is Confirmed'        , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_time'       , 26, 'Confirmed Time'      , 'Confirmed Time'      , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_user'       , 27, 'Confirmed USer'      , 'Confirmed USer'      , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_cfm_sent'    , 28, 'Is Confirmation Sent', 'Is Confirmation Sent', 0, 0, 0, '', 0,   0, 0, '', 1, 28, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'sent_time'      , 29, 'Sent Time'           , 'Sent Time'           , 0, 0, 0, '', 0,   0, 0, '', 1, 29, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'sent_user'      , 30, 'Sent User'           , 'Sent User'           , 0, 0, 0, '', 0,   0, 0, '', 1, 30, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'        , 31, 'Loguser'             , 'Loguser'             , 0, 0, 0, '', 0,   0, 0, '', 0, 31, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'        , 32, 'Logtime'             , 'Logtime'             , 0, 0, 0, '', 0,   0, 0, '', 0, 32, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'tra_mm';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table tra_mm Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\???P?w?s\FX\tra_pair.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-10-16
 內容 : tra_pair
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_tra_pair] (
	[child]        		VARCHAR(13) NOT NULL,
	[parent]       		VARCHAR(13) NOT NULL,
	[type]         		SMALLINT NOT NULL,
	[matching_type]		SMALLINT NOT NULL,
	[amt_allocation]	DECIMAL(20,5) NOT NULL,
	[loguser]      		VARCHAR(20) NOT NULL,
	[logtime]      		DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_pair]') AND type in (N'U'))
	EXEC sp_backup_data 'tra_pair', 'Tmp_tra_pair'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[tra_pair]') AND type in (N'U'))
	DROP TABLE tra_pair;

EXEC sp_rename 'Tmp_tra_pair', 'tra_pair', 'OBJECT'
GO

ALTER TABLE [dbo].[tra_pair] ADD CONSTRAINT [PK_tra_pair] PRIMARY KEY CLUSTERED
(
    [child]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'tra_pair', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'tra_pair', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '配對';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'child'			,  1, 'Deal Number'		 , 'Deal Number'		, 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'parent'			,  2, 'Deal Number'		 , 'Deal Number'		, 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'type'			,  3, 'Product Type'	 , 'Product Type'		, 0, 0, 0, '', 0,   8, 0, '', 1,  3, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'matching_type'	,  4, 'Matching Type'	 , 'Matching Type'		, 0, 0, 0, '', 0,   9, 0, '', 1,  4, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'amt_allocation'	,  5, 'Allocation Amount', 'Allocation Amount'	, 0, 0, 0, '', 0,   9, 0, '', 1,  5, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'			,  6, 'Loguser'			 , 'Loguser'			, 0, 0, 0, '', 0,   0, 0, '', 0,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'			,  7, 'Logtime'			 , 'Logtime'			, 0, 0, 0, '', 0,   0, 0, '', 0,  7, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'tra_pair';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table tra_pair Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?@?~?y?{\pro_date.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Henry
 日期 : 2013-11-26
 內容 : pro_date
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_pro_date] (
	[pno]     	INT NOT NULL,
	[proctp]  	SMALLINT NOT NULL,
	[native]  	SMALLINT NOT NULL,
	[excdate] 	SMALLDATETIME NOT NULL,
	[procuser]	NVARCHAR(20) NOT NULL,
	[proctime]	DATETIME NOT NULL,
	[isend]     	BIT NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[pro_date]') AND type in (N'U'))
	EXEC sp_backup_data 'pro_date', 'Tmp_pro_date'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[pro_date]') AND type in (N'U'))
	DROP TABLE pro_date;

EXEC sp_rename 'Tmp_pro_date', 'pro_date', 'OBJECT'
GO

ALTER TABLE [dbo].[pro_date] ADD CONSTRAINT [PK_pro_date] PRIMARY KEY CLUSTERED
(
	[pno],[proctp],[native]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'pro_date', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'pro_date', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '投組流程控制檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'pno'     ,  1, '契約內碼', '契約內碼', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'proctp'  ,  2, '流程類型', '流程類型', 1, 1, 0, '', 0,  72, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'native'  ,  3, '國內外'  , '國內外'  , 1, 1, 0, '', 0,  74, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'excdate' ,  4, '作業日期', '作業日期', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'procuser',  5, '執行人員', '執行人員', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'proctime',  6, '執行時間', '執行時間', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'isend'     ,  7, '結束點'  , '結束點'  , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'pro_date';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;



IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table pro_date Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\afos_ibs_template.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-20
 內容 : afos_ibs_template
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_ibs_template] (
	[pno]    	INT NOT NULL,
	[ccy]    	CHAR(3) NOT NULL,
	[name]   	NVARCHAR(200) NOT NULL,
	[loguser]	VARCHAR(20) NOT NULL,
	[logtime]	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_ibs_template]') AND type in (N'U'))
	EXEC sp_backup_data 'afos_ibs_template', 'Tmp_afos_ibs_template'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_ibs_template]') AND type in (N'U'))
	DROP TABLE afos_ibs_template;	
	
EXEC sp_rename 'Tmp_afos_ibs_template', 'afos_ibs_template', 'OBJECT'
GO	

ALTER TABLE [dbo].[afos_ibs_template] ADD CONSTRAINT [PK_afos_ibs_template] PRIMARY KEY CLUSTERED
(
	[pno],[ccy]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'afos_ibs_template', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_ibs_template', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'IBS Template';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'pno'    ,  1, '客戶代碼'     , '客戶代碼'     , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy'    ,  2, 'Currency'     , 'Currency'     , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'   ,  3, 'Template Name', 'Template Name', 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser',  4, 'Loguser'      , 'Loguser'      , 0, 0, 0, '', 0,   0, 0, '', 0,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime',  5, 'Logtime'      , 'Logtime'      , 0, 0, 0, '', 0,   0, 0, '', 0,  5, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_ibs_template';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_ibs_template Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_account.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-19
 內容 : cmn_account
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_account] (
	[ano]         	INT NOT NULL,
	[account_no]  	VARCHAR(16) NOT NULL,
	[account_name]	NVARCHAR(200) NOT NULL,
	[country]     	VARCHAR(5) NOT NULL,
	[location]    	VARCHAR(5) NOT NULL,
	[ccy]         	CHAR(3) NOT NULL,
	[broker]      	VARCHAR(12) NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_account]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_account', 'Tmp_cmn_account'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_account]') AND type in (N'U'))
	DROP TABLE cmn_account;	
	
EXEC sp_rename 'Tmp_cmn_account', 'cmn_account', 'OBJECT'
GO	

ALTER TABLE [dbo].[cmn_account] ADD CONSTRAINT [PK_cmn_account] PRIMARY KEY CLUSTERED
(
	[ano]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_account', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_account', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'SSB Account';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'ano'         ,  1, '帳號代碼'    , '帳號代碼'    , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'account_no'  ,  2, 'Account No'  , 'Account No'  , 0, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'account_name',  3, 'Account Name', 'Account Name', 0, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'country'     ,  4, 'Domicile'    , 'Domicile'    , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'location'    ,  5, 'Location'    , 'Location'    , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy'         ,  6, 'Currency'    , 'Currency'    , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'broker'      ,  7, 'BIC'   , 'BIC'   , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  8, 'Loguser'     , 'Loguser'     , 0, 0, 0, '', 0,   0, 0, '', 0,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     ,  9, 'Logtime'     , 'Logtime'     , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_account';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_account Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_account_balance.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-04
 內容 : cmn_account_balance
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_account_balance] (
	[ano]    	INT NOT NULL,
	[date]   	DATE NOT NULL,
	[amount] 	NUMERIC(20,5) NOT NULL,
	[loguser]	VARCHAR(20) NOT NULL,
	[logtime]	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_account_balance]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_account_balance', 'Tmp_cmn_account_balance'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_account_balance]') AND type in (N'U'))
	DROP TABLE cmn_account_balance;	
	
EXEC sp_rename 'Tmp_cmn_account_balance', 'cmn_account_balance', 'OBJECT'
GO	

ALTER TABLE [dbo].[cmn_account_balance] ADD CONSTRAINT [PK_cmn_account_balance] PRIMARY KEY CLUSTERED
(
	[ano], [date]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_account_balance', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_account_balance', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'SSB Account Balance';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'ano'    ,  1, '帳號代碼', '帳號代碼', 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date'   ,  2, 'Date'    , 'Date'    , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'amount' ,  3, 'Amount'  , 'Amount'  , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser',  6, 'Loguser' , 'Loguser' , 0, 0, 0, '', 0,   0, 0, '', 0,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime',  7, 'Logtime' , 'Logtime' , 0, 0, 0, '', 0,   0, 0, '', 0,  7, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_account_balance';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_account_balance Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_broker.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-05
 內容 : cmn_broker
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_broker] (
	[broker]   	VARCHAR(12) NOT NULL,
	[bic]      	VARCHAR(15) NOT NULL,
	[type]     	SMALLINT NOT NULL,
	[cname]    	NVARCHAR(100) NOT NULL,
	[cbrief]   	NVARCHAR(100) NOT NULL,
	[ename]    	VARCHAR(100) NOT NULL,
	[ebrief]   	VARCHAR(100) NOT NULL,
	[head]     	VARCHAR(3) NOT NULL,
	[branch]   	VARCHAR(4) NOT NULL,
	[is_head]  	BIT NOT NULL,
	[address]  	NVARCHAR(200) NOT NULL,
	[area_code]	SMALLINT NOT NULL,
	[phone]    	VARCHAR(20) NOT NULL,
	[accode]   	VARCHAR(10) NOT NULL,
	[loguser]  	VARCHAR(20) NOT NULL,
	[logtime]  	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_broker]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_broker', 'Tmp_cmn_broker'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_broker]') AND type in (N'U'))
	DROP TABLE cmn_broker;	
	
EXEC sp_rename 'Tmp_cmn_broker', 'cmn_broker', 'OBJECT'
GO	

ALTER TABLE [dbo].[cmn_broker] ADD CONSTRAINT [PK_cmn_broker] PRIMARY KEY CLUSTERED
(
	[broker]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_broker', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_broker', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'FISC Inistitutions';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'broker'   ,  1, 'broker' , 'broker' , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'bic'      ,  2, 'BIC'               , 'BIC'               , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'type'     ,  3, 'Type'              , 'Type'              , 0, 0, 0, '', 0,  33, 0, '', 1,  3, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname'    ,  4, 'Chinese Name'      , 'Chinese Name'      , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbrief'   ,  5, 'Chinese Brief Name', 'Chinese Brief Name', 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ename'    ,  6, 'English Name'      , 'English Name'      , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ebrief'   ,  7, 'English Brief Name', 'English Brief Name', 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'head'     ,  8, 'Head'              , 'Head'              , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'branch'   ,  9, 'Branch'            , 'Branch'            , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_head'  , 10, 'Is Head'           , 'Is Head'           , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'address'  , 11, 'Address'           , 'Address'           , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'area_code', 12, 'Area Code'         , 'Area Code'         , 0, 0, 0, '', 0,  -1, 0, '', 1, 12, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'phone'    , 13, 'Phone Number'      , 'Phone Number'      , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'accode'   , 14, 'Accode'            , 'Accode'            , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'  , 15, 'Loguser'           , 'Loguser'           , 0, 0, 0, '', 0,   0, 0, '', 0, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'  , 16, 'Logtime'           , 'Logtime'           , 0, 0, 0, '', 0,   0, 0, '', 0, 16, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_broker';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_broker Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_calendar.sql"  
--this script is created by SpecCreator
/*---------------------------------
 版本 : 1
 日期 : 2013-10-24
 內容 : cmn_calendar
---------------------------------*/
BEGIN TRANSACTION 

--1.建立新Table
CREATE TABLE [dbo].[Tmp_cmn_calendar] (
	[country] 	VARCHAR(5) NOT NULL,
	[date]    	SMALLDATETIME NOT NULL,
	[tradecal]	BIT NOT NULL,
	[moneycal]	BIT NOT NULL,
	[loguser] 	VARCHAR(20) NOT NULL,
	[logtime] 	DATETIME NOT NULL	
);
  
--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_calendar]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_calendar', 'Tmp_cmn_calendar'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_calendar]') AND type in (N'U'))
	DROP TABLE cmn_calendar;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_cmn_calendar', 'cmn_calendar', 'OBJECT'
GO

ALTER TABLE [dbo].[cmn_calendar] ADD CONSTRAINT [PK_cmn_calendar] PRIMARY KEY CLUSTERED
(
	[country],[date]
)   
ON [PRIMARY]
GO

--6.完成(買單).....
COMMIT;

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_calendar', 'ALL';

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_calendar', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'country' ,  1, '國別'    , '國別'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date'    ,  2, '日期'    , '日期'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tradecal',  3, '交易市場', '交易市場', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'moneycal',  4, '金融機構', '金融機構', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser' ,  5, '異動人員', '異動人員', 0, 0, 0, '', 0,   0, 0, '', 0, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime' ,  6, '異動時間', '異動時間', 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1 
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--將欄位次序調整成與 Table Scheme 相同
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_calendar';

--更新欄位選項及說明
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END 
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;  
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT '更新 cmn_calendar 結束!'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_calendar_setting.sql"  
--this script is created by SpecCreator
/*---------------------------------
 版本 : 1
 日期 : 2013-10-24
 內容 : cmn_calendar_setting
---------------------------------*/
BEGIN TRANSACTION 

--1.建立新Table
CREATE TABLE [dbo].[Tmp_cmn_calendar_setting] (
	[calendar_catalog]	SMALLINT NOT NULL,
    [target]	VARCHAR (10) NOT NULL,
	[date]   	DATE NOT NULL,
	[date_type]   	SMALLINT NOT NULL,
	[name]   	NVARCHAR(40) NOT NULL,
	[note]   	NVARCHAR(200) NOT NULL,
	[loguser]	VARCHAR(20) NOT NULL,
	[logtime]	DATETIME NOT NULL


);
  
--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_calendar_setting]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_calendar_setting', 'Tmp_cmn_calendar_setting'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_calendar_setting]') AND type in (N'U'))
	DROP TABLE cmn_calendar_setting;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_cmn_calendar_setting', 'cmn_calendar_setting', 'OBJECT'
GO

ALTER TABLE [dbo].[cmn_calendar_setting] ADD CONSTRAINT [PK_cmn_calendar_setting] PRIMARY KEY CLUSTERED
(
	[calendar_catalog], [target], [date]
)   
ON [PRIMARY]
GO

--6.完成(買單).....
COMMIT;

--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_calendar_setting', 'ALL';

--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_calendar_setting', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Calendar Setting';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'calendar_catalog',  1, 'Calendar Catalog', 'Calendar Catalog', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'target'          ,  2, 'Target'          , 'Target'          , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date'            ,  2, 'Date'            , 'Date'            , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date_type'       ,  3, 'Date Type'       , 'Date Type'       , 0, 0, 0, '', 0,   4, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'            ,  4, 'Date Name'       , 'Date Name'       , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'            ,  5, 'Notes'           , 'Notes'           , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'         ,  6, 'Loguser'         , 'Loguser'         , 0, 0, 0, '', 0,   0, 0, '', 0, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'         ,  7, 'Logtime'         , 'Logtime'         , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1 
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--將欄位次序調整成與 Table Scheme 相同
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_calendar_setting';

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT '更新 cmn_calendar_setting 結束!'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_cbc_accounts.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-05
 內容 : cmn_cbc_accounts
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_cbc_accounts] (
	[cbc_acc_no]	VARCHAR(4) NOT NULL,
	[cname]     	NVARCHAR(100) NOT NULL,
	[ename]     	VARCHAR(100) NOT NULL,
	[broker]    	VARCHAR(12) NOT NULL,
	[open_date] 	DATE NOT NULL,
	[loguser]   	VARCHAR(20) NOT NULL,
	[logtime]   	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_cbc_accounts]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_cbc_accounts', 'Tmp_cmn_cbc_accounts'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_cbc_accounts]') AND type in (N'U'))
	DROP TABLE cmn_cbc_accounts;	
	
EXEC sp_rename 'Tmp_cmn_cbc_accounts', 'cmn_cbc_accounts', 'OBJECT'
GO	

ALTER TABLE [dbo].[cmn_cbc_accounts] ADD CONSTRAINT [PK_cmn_cbc_accounts] PRIMARY KEY CLUSTERED
(
	[cbc_acc_no]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_cbc_accounts', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_cbc_accounts', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'CBC Accounts';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'cbc_acc_no',  1, 'CBC Account No', 'CBC Account No', 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname'     ,  2, 'Chinese Name'  , 'Chinese Name'  , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ename'     ,  3, 'English Name'  , 'English Name'  , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'broker'    ,  4, 'Inistution No' , 'Inistution No' , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'open_date' ,  5, 'Open Date'     , 'Open Date'     , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'   , 15, 'Loguser'       , 'Loguser'       , 0, 0, 0, '', 0,   0, 0, '', 0, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'   , 16, 'Logtime'       , 'Logtime'       , 0, 0, 0, '', 0,   0, 0, '', 0, 16, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_cbc_accounts';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_cbc_accounts Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_ccy_price.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-20
 內容 : cmn_ccy_price
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_ccy_price] (
	[date]           	DATE NOT NULL,
	[ccy]            	CHAR(3) NOT NULL,
	[rate_buy]       	NUMERIC(20,10) NOT NULL,
	[rate_sell]      	NUMERIC(20,10) NOT NULL,
	[rate_avg]       	NUMERIC(20,10) NOT NULL,
	[rate_exchg]     	NUMERIC(20,10) NOT NULL,
	[calculated_type]	SMALLINT NOT NULL,
	[rate]           	NUMERIC(20,10) NOT NULL,
	[loguser]        	VARCHAR(20) NOT NULL,
	[logtime]        	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_ccy_price]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_ccy_price', 'Tmp_cmn_ccy_price'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_ccy_price]') AND type in (N'U'))
	DROP TABLE cmn_ccy_price;	
	
EXEC sp_rename 'Tmp_cmn_ccy_price', 'cmn_ccy_price', 'OBJECT'
GO	

ALTER TABLE [dbo].[cmn_ccy_price] ADD CONSTRAINT [PK_cmn_ccy_price] PRIMARY KEY CLUSTERED
(
	[date],[ccy]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_ccy_price', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_ccy_price', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Exchange Rate';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'date'           ,  1, 'Date'           , 'Date'           , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy'            ,  2, 'Currency'       , 'Currency'       , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rate_buy'       ,  3, 'Buy Rate'       , 'Buy Rate'       , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rate_sell'      ,  4, 'Sell Rate'      , 'Sell Rate'      , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rate_avg'       ,  5, 'Avg. Rate'      , 'Avg. Rate'      , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rate_exchg'     ,  6, 'Exchg Rate'     , 'Exchg Rate'     , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'calculated_type',  7, 'Calculated Type', 'Calculated Type', 0, 0, 0, '', 0,  27, 0, '', 1,  7, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rate'           ,  8, 'Calculated Rate', 'Calculated Rate', 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'        ,  9, 'Loguser'        , 'Loguser'        , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'        , 10, 'Logtime'        , 'Logtime'        , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_ccy_price';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_ccy_price Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_country.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-07-05
 內容 : cmn_country
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_country] (
	[country]     	VARCHAR(5) NOT NULL,
	[cname]       	NVARCHAR(20) NOT NULL,
	[ename]       	VARCHAR(50) NOT NULL,
	[area_code]	    SMALLINT NOT NULL,
	[accode]      	VARCHAR(10) NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_country]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_country', 'Tmp_cmn_country'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_country]') AND type in (N'U'))
	DROP TABLE cmn_country;

EXEC sp_rename 'Tmp_cmn_country', 'cmn_country', 'OBJECT'
GO

ALTER TABLE [dbo].[cmn_country] ADD CONSTRAINT [PK_cmn_country] PRIMARY KEY CLUSTERED
(
    [country]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_country', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_country', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Country';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'country'     ,  1, 'Country'        , 'Country'        , 1, 1, 0, '', 0,   0, 1, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname'       ,  2, 'Chinese Name'   , 'Chinese Name'   , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ename'       ,  3, 'English Name'   , 'English Name'   , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'area_code'   ,  6, 'Area Code'      , 'Area Code'      , 0, 0, 0, '', 0,  -1, 0, '', 1,  6, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'accode'      ,  8, 'Accode'         , 'Accode'         , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  9, 'Loguser'        , 'Loguser'        , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     , 10, 'Logtime'        , 'Logtime'        , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_country';

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_country Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_currency.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-04
 內容 : cmn_currency
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_currency] (
	[ccy]         	CHAR(3) NOT NULL,
	[name]        	VARCHAR(40) NOT NULL,
	[cname]       	NVARCHAR(40) NOT NULL,
	[country]     	VARCHAR(5) NOT NULL,
	[sign]        	VARCHAR(3) NOT NULL,
	[ccy_code]    	VARCHAR(3) NOT NULL,
	[holiday_type]	SMALLINT NOT NULL,
	[amtdgt]      	INT NOT NULL,
	[ratedgt]     	INT NOT NULL,
	[exchdgt]     	INT NOT NULL,
	[qtydgt]      	INT NOT NULL,
	[accode]      	VARCHAR(10) NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_currency]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_currency', 'Tmp_cmn_currency'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_currency]') AND type in (N'U'))
	DROP TABLE cmn_currency;	
	
EXEC sp_rename 'Tmp_cmn_currency', 'cmn_currency', 'OBJECT'
GO	

ALTER TABLE [dbo].[cmn_currency] ADD CONSTRAINT [PK_cmn_currency] PRIMARY KEY CLUSTERED
(
	[ccy]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_currency', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_currency', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Currency';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'ccy'         ,  1, 'Currency'      , 'Currency'      , 1, 1, 0, '', 0,   0, 1, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'        ,  2, 'English Name'  , 'English Name'  , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname'       ,  3, 'Chinese Name'  , 'Chinese Name'  , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'country'     ,  4, 'Country'       , 'Country'       , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'sign'        ,  5, 'CURRSIGN'      , 'CURRSIGN'      , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy_code'    ,  6, 'CURRCODE'      , 'CURRCODE'      , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'holiday_type',  7, 'Holiday Type'  , 'Holiday Type'  , 0, 0, 0, '', 0,  29, 0, '', 1,  7, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'amtdgt'      ,  8, 'Amount Digit'  , 'Amount Digit'  , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ratedgt'     ,  9, 'Interest Digit', 'Interest Digit', 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'exchdgt'     , 10, 'Rate Digit'    , 'Rate Digit'    , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'qtydgt'      , 11, 'Quantity Digit', 'Quantity Digit', 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'accode'      , 12, 'Accode'        , 'Accode'        , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     , 13, 'Loguser'       , 'Loguser'       , 0, 0, 0, '', 0,   0, 0, '', 0, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     , 14, 'Logtime'       , 'Logtime'       , 0, 0, 0, '', 0,   0, 0, '', 0, 14, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_currency';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_currency Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_otc_broker.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-04
 內容 : cmn_otc_broker
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_otc_broker] (
	[broker] 	VARCHAR(12) NOT NULL,
	[cname]  	NVARCHAR(100) NOT NULL,
	[ename]  	VARCHAR(100) NOT NULL,
	[loguser]	VARCHAR(20) NOT NULL,
	[logtime]	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_otc_broker]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_otc_broker', 'Tmp_cmn_otc_broker'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_otc_broker]') AND type in (N'U'))
	DROP TABLE cmn_otc_broker;	
	
EXEC sp_rename 'Tmp_cmn_otc_broker', 'cmn_otc_broker', 'OBJECT'
GO	

ALTER TABLE [dbo].[cmn_otc_broker] ADD CONSTRAINT [PK_cmn_otc_broker] PRIMARY KEY CLUSTERED
(
	[broker]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_otc_broker', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_otc_broker', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'OTC Institutions';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'broker' ,  1, 'Institution Code', 'Institution Code', 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname'  ,  2, 'Chinese Name'    , 'Chinese Name'    , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ename'  ,  3, 'English Name'    , 'English Name'    , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser',  4, 'Loguser'         , 'Loguser'         , 0, 0, 0, '', 0,   0, 0, '', 0,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime',  5, 'Logtime'         , 'Logtime'         , 0, 0, 0, '', 0,   0, 0, '', 0,  5, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_otc_broker';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_otc_broker Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?򥻸?\cmn_tibor.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-10-24
 內容 : cmn_tibor
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cmn_tibor] (
	[date]   	DATE NOT NULL,
	[rate]   	NUMERIC(20,10) NOT NULL,
	[loguser]	VARCHAR(20) NOT NULL,
	[logtime]	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_tibor]') AND type in (N'U'))
	EXEC sp_backup_data 'cmn_tibor', 'Tmp_cmn_tibor'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cmn_tibor]') AND type in (N'U'))
	DROP TABLE cmn_tibor;	
	
EXEC sp_rename 'Tmp_cmn_tibor', 'cmn_tibor', 'OBJECT'
GO	

ALTER TABLE [dbo].[cmn_tibor] ADD CONSTRAINT [PK_cmn_tibor] PRIMARY KEY CLUSTERED
(
	[date]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cmn_tibor', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cmn_tibor', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'TIBOR';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'date'   ,  1, 'Date'    , 'Date'    , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rate'   ,  2, 'TIBOR(%)', 'TIBOR(%)', 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser',  3, 'Loguser' , 'Loguser' , 0, 0, 0, '', 0,   0, 0, '', 0,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime',  4, 'Logtime' , 'Logtime' , 0, 0, 0, '', 0,   0, 0, '', 0,  4, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cmn_tibor';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cmn_tibor Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????cb_cashflow.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Betsy
 日期 : 2017-11-24
 內容 : cb_cashflow
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cb_cashflow] (
	[pno]           	INT NOT NULL,
	[date]          	DATE NOT NULL,
	[seq]           	INT NOT NULL,
	[trade_no]      	VARCHAR(13) NOT NULL,
	[value_date]    	DATE NOT NULL,
	[cp_type]       	SMALLINT NOT NULL,
	[product_type]  	SMALLINT NOT NULL,
	[swap_sf]       	SMALLINT NOT NULL,
	[type]          	SMALLINT NOT NULL,
	[trade_status]  	SMALLINT NOT NULL,
	[orig_trade_no] 	VARCHAR(13) NOT NULL,
	[orig_trade_amt]	NUMERIC(20,5) NOT NULL,
	[trade_type]    	SMALLINT NOT NULL,
	[cb_trade_type] 	CHAR(1) NOT NULL,
	[ccy]           	CHAR(3) NOT NULL,
	[amt_in]        	NUMERIC(20,5) NOT NULL,
	[amt_out]       	NUMERIC(20,5) NOT NULL,
	[exch_rate]     	NUMERIC(11,8) NOT NULL,
	[bal_amt]       	NUMERIC(20,5) NOT NULL,
	[note]          	VARCHAR(100) NOT NULL,
	[data_no]       	VARCHAR(12) NOT NULL,
	[country_source]	VARCHAR(5) NOT NULL,
	[class]         	VARCHAR(3) NOT NULL,
	[class_detail]  	VARCHAR(3) NOT NULL,
	[kind_code]     	VARCHAR(3) NOT NULL,
	[forward_spl]   	VARCHAR(3) NOT NULL,
	[data_source]   	VARCHAR(3) NOT NULL,
	[data_kind]     	VARCHAR(3) NOT NULL,
	[oppo_name]     	VARCHAR(40) NOT NULL,
	[rem_type]      	VARCHAR(3) NOT NULL,
	[swift_bank]    	VARCHAR(16) NOT NULL,
	[approv_no_flag]	VARCHAR(1) NOT NULL,
	[forward_settle]	VARCHAR(3) NOT NULL,
	[data_source2]  	VARCHAR(1) NOT NULL,
	[bank]          	VARCHAR(12) NOT NULL,
	[bankacc]       	VARCHAR(14) NOT NULL,
	[cp_bank]       	VARCHAR(12) NOT NULL,
	[cp_bankacc]    	VARCHAR(14) NOT NULL,
	[putdate]       	SMALLDATETIME NOT NULL,
	[rcdate]        	SMALLDATETIME NOT NULL,
	[loguser]       	VARCHAR(20) NOT NULL,
	[logtime]       	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_cashflow]') AND type in (N'U'))
	EXEC sp_backup_data 'cb_cashflow', 'Tmp_cb_cashflow'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_cashflow]') AND type in (N'U'))
	DROP TABLE cb_cashflow;	
	
EXEC sp_rename 'Tmp_cb_cashflow', 'cb_cashflow', 'OBJECT'
GO	

ALTER TABLE [dbo].[cb_cashflow] ADD CONSTRAINT [PK_cb_cashflow] PRIMARY KEY CLUSTERED
(
	[pno],[date],[seq]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cb_cashflow', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cb_cashflow', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '央行申報資金檔';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'pno'           ,  1, 'Pno'              , 'Pno'              , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date'          ,  2, 'Date'             , 'Date'             , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'seq'           ,  3, 'Sequence No'      , 'Sequence No'      , 1, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_no'      ,  4, 'Trade No'         , 'Trade No'         , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'value_date'    ,  5, 'Value Date'       , 'Value Date'       , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cp_type'       ,  6, 'Counterparty Type', 'Counterparty Type', 0, 0, 0, '', 0, 501, 0, '', 1,  6, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'product_type'  ,  7, 'Product'          , 'Product'          , 0, 0, 0, '', 0,  73, 0, '', 1,  7, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'swap_sf'       ,  8, 'SWAP S/F'         , 'SWAP S/F'         , 0, 0, 0, '', 0,  75, 0, '', 1,  8, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'type'          ,  9, 'Product Type'     , 'Product Type'     , 0, 0, 0, '', 0,   8, 0, '', 1,  9, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_status'  , 10, 'Trade Status'     , 'Trade Status'     , 0, 0, 0, '', 0,  76, 0, '', 1, 10, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'orig_trade_no' , 11, 'Orig Deal Number' , 'Orig Deal Number' , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'orig_trade_amt', 12, 'Orig Deal Amount' , 'Orig Deal Amount' , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_type'    , 13, 'Trade Type'       , 'Trade Type'       , 0, 0, 0, '', 0,   2, 0, '', 1, 13, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cb_trade_type' , 14, 'CB Trade Type'    , 'CB Trade Type'    , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ccy'           , 15, 'Currency'         , 'Currency'         , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'amt_in'        , 16, 'Inward Amount'    , 'Inward Amount'    , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'amt_out'       , 17, 'Outward Amount'   , 'Outward Amount'   , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'exch_rate'     , 18, 'Rate'             , 'Rate'             , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'bal_amt'       , 19, '餘額'             , '餘額'             , 0, 0, 0, '', 0,   0, 0, '', 1, 19, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'          , 20, 'Remark'           , 'Remark'           , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'data_no'       , 21, 'Data No'          , 'Data No'          , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'country_source', 22, 'Country Source'   , 'Country Source'   , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'class'         , 23, 'Class'            , 'Class'            , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'class_detail'  , 24, 'Class Detail'     , 'Class Detail'     , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'kind_code'     , 25, 'Kind Code'        , 'Kind Code'        , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'forward_spl'   , 26, 'Forward Spl'      , 'Forward Spl'      , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'data_source'   , 27, '外匯來源及去處'   , '外匯來源及去處'   , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'data_kind'     , 28, 'Data Kind'        , 'Data Kind'        , 0, 0, 0, '', 0,   0, 0, '', 1, 28, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'oppo_name'     , 29, 'Oppo Name'        , 'Oppo Name'        , 0, 0, 0, '', 0,   0, 0, '', 1, 29, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rem_type'      , 30, 'Rem Type'         , 'Rem Type'         , 0, 0, 0, '', 0,   0, 0, '', 1, 30, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'swift_bank'    , 31, 'Swift Bank'       , 'Swift Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 31, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'approv_no_flag', 32, 'Approval No Flag' , 'Approval No Flag' , 0, 0, 0, '', 0,   0, 0, '', 1, 32, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'forward_settle', 33, 'Forward Settle'   , 'Forward Settle'   , 0, 0, 0, '', 0,   0, 0, '', 1, 33, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'data_source2'  , 34, 'Data Source'      , 'Data Source'      , 0, 0, 0, '', 0,   0, 0, '', 1, 34, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'bank'          , 35, '保管專戶銀行代號' , '保管專戶銀行代號' , 0, 0, 0, '', 0,   0, 0, '', 1, 35, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'bankacc'       , 36, '保管專戶銀行帳號' , '保管專戶銀行帳號' , 0, 0, 0, '', 0,   0, 0, '', 1, 36, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cp_bank'       , 37, '交割專戶銀行代號' , '交割專戶銀行代號' , 0, 0, 0, '', 0,   0, 0, '', 1, 37, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cp_bankacc'    , 38, '交割專戶銀行帳號' , '交割專戶銀行帳號' , 0, 0, 0, '', 0,   0, 0, '', 1, 38, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'putdate'       , 39, '產檔日期'         , '產檔日期'         , 0, 0, 0, '', 0,   0, 0, '', 1, 39, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rcdate'        , 40, '收檔日期'         , '收檔日期'         , 0, 0, 0, '', 0,   0, 0, '', 1, 40, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'       , 41, '異動人員'         , '異動人員'         , 0, 0, 0, '', 0,   0, 0, '', 0, 41, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'       , 42, '異動時間'         , '異動時間'         , 0, 0, 0, '', 0,   0, 0, '', 0, 42, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cb_cashflow';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cb_cashflow Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????cb_report_01.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Betsy
 日期 : 2017-11-21
 內容 : cb_report_01
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cb_report_01] (
	[pno]           	INT NOT NULL,
	[date]          	DATE NOT NULL,
	[seq]           	INT NOT NULL,
	[source]        	VARCHAR(3) NOT NULL,
	[note]          	VARCHAR(100) NOT NULL,
	[exch_rate]     	NUMERIC(11,8) NOT NULL,
	[total_amt]     	NUMERIC(20,5) NOT NULL,
	[forward_settle]	VARCHAR(3) NOT NULL,
	[JOB-CODE]      	CHAR(1) NOT NULL,
	[CURR]          	CHAR(3) NOT NULL,
	[BANK]          	CHAR(4) NOT NULL,
	[SER-NO]        	CHAR(5) NOT NULL,
	[REM-TYPE]      	CHAR(1) NOT NULL,
	[OP-DATE]       	CHAR(8) NOT NULL,
	[DATA-NO]       	CHAR(12) NOT NULL,
	[BAN-IDNO]      	CHAR(10) NOT NULL,
	[BIRTH-DATE]    	CHAR(8) NOT NULL,
	[ISSUE-DATE]    	CHAR(8) NOT NULL,
	[EXP-DATE]      	CHAR(8) NOT NULL,
	[KIND-CODE]     	CHAR(1) NOT NULL,
	[DATA-KIND]     	CHAR(1) NOT NULL,
	[DATA-AMT-SIGN] 	CHAR(1) NOT NULL,
	[DATA-AMT]      	CHAR(14) NOT NULL,
	[FORWARD-SPL]   	CHAR(1) NOT NULL,
	[CLASS]         	CHAR(3) NOT NULL,
	[TOP]           	CHAR(1) NOT NULL,
	[690-SUB-CODE]  	CHAR(1) NOT NULL,
	[CNTRY]         	CHAR(2) NOT NULL,
	[NO-REP-FLAG]   	CHAR(1) NOT NULL,
	[Q-ID]          	CHAR(2) NOT NULL,
	[NATURAL]       	CHAR(1) NOT NULL,
	[APROV-NO-FLAG] 	CHAR(1) NOT NULL,
	[SPEC-BANK]     	CHAR(4) NOT NULL,
	[DOCU-NO]       	CHAR(7) NOT NULL,
	[NT-EXCHG-RATE] 	CHAR(11) NOT NULL,
	[OPPO-NAME]     	CHAR(40) NOT NULL,
	[SWIFT-BANK]    	CHAR(11) NOT NULL,
	[OPPO-BANK]     	CHAR(60) NOT NULL,
	[DATA-SOURCE]   	CHAR(1) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_01]') AND type in (N'U'))
	EXEC sp_backup_data 'cb_report_01', 'Tmp_cb_report_01'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_01]') AND type in (N'U'))
	DROP TABLE cb_report_01;	
	
EXEC sp_rename 'Tmp_cb_report_01', 'cb_report_01', 'OBJECT'
GO	

ALTER TABLE [dbo].[cb_report_01] ADD CONSTRAINT [PK_cb_report_01] PRIMARY KEY CLUSTERED
(
	[pno],[date],[seq]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cb_report_01', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cb_report_01', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '外匯收入資料傳輸檔案格式';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'pno'           ,  1, 'Pno'             , 'Pno'             , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date'          ,  2, 'Date'            , 'Date'            , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'seq'           ,  3, 'Sequence No'     , 'Sequence No'     , 1, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source'        ,  4, 'Source'          , 'Source'          , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'          ,  5, 'Remark'          , 'Remark'          , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'exch_rate'     ,  6, 'Rate'            , 'Rate'            , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'total_amt'     ,  7, 'Total Amount'    , 'Total Amount'    , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'forward_settle',  8, 'Forward Settle'  , 'Forward Settle'  , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'JOB-CODE'      ,  9, 'Job Code'        , 'Job Code'        , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CURR'          , 10, 'Ccy'             , 'Ccy'             , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BANK'          , 11, 'Bank'            , 'Bank'            , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SER-NO'        , 12, 'Ser No'          , 'Ser No'          , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'REM-TYPE'      , 13, 'Rem Type'        , 'Rem Type'        , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OP-DATE'       , 14, 'Op Date'         , 'Op Date'         , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-NO'       , 15, 'Data No'         , 'Data No'         , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BAN-IDNO'      , 16, 'Ban Idno'        , 'Ban Idno'        , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BIRTH-DATE'    , 17, 'Birth Date'      , 'Birth Date'      , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ISSUE-DATE'    , 18, 'Issue Date'      , 'Issue Date'      , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'EXP-DATE'      , 19, 'Expire Date'     , 'Expire Date'     , 0, 0, 0, '', 0,   0, 0, '', 1, 19, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'KIND-CODE'     , 20, 'Kind Code'       , 'Kind Code'       , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-KIND'     , 21, 'Data Kind'       , 'Data Kind'       , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-AMT-SIGN' , 22, 'Data Amt Sign'   , 'Data Amt Sign'   , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-AMT'      , 23, 'Data Amount'     , 'Data Amount'     , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'FORWARD-SPL'   , 24, 'Forward Spl'     , 'Forward Spl'     , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CLASS'         , 25, 'Class'           , 'Class'           , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'TOP'           , 26, 'Top'             , 'Top'             , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, '690-SUB-CODE'  , 27, 'Sub Code'        , 'Sub Code'        , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CNTRY'         , 28, 'Cntry'           , 'Cntry'           , 0, 0, 0, '', 0,   0, 0, '', 1, 28, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NO-REP-FLAG'   , 29, 'No Rep Flag'     , 'No Rep Flag'     , 0, 0, 0, '', 0,   0, 0, '', 1, 29, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'Q-ID'          , 30, 'Q Id'            , 'Q Id'            , 0, 0, 0, '', 0,   0, 0, '', 1, 30, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NATURAL'       , 31, 'Natural'         , 'Natural'         , 0, 0, 0, '', 0,   0, 0, '', 1, 31, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'APROV-NO-FLAG' , 32, 'Approval No Flag', 'Approval No Flag', 0, 0, 0, '', 0,   0, 0, '', 1, 32, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SPEC-BANK'     , 33, 'Spec Bank'       , 'Spec Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 33, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DOCU-NO'       , 34, 'Docu No'         , 'Docu No'         , 0, 0, 0, '', 0,   0, 0, '', 1, 34, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NT-EXCHG-RATE' , 35, 'Nt Exchg Rate'   , 'Nt Exchg Rate'   , 0, 0, 0, '', 0,   0, 0, '', 1, 35, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OPPO-NAME'     , 36, 'Oppo Name'       , 'Oppo Name'       , 0, 0, 0, '', 0,   0, 0, '', 1, 36, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SWIFT-BANK'    , 37, 'Swift Bank'      , 'Swift Bank'      , 0, 0, 0, '', 0,   0, 0, '', 1, 37, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OPPO-BANK'     , 38, 'Oppo Bank'       , 'Oppo Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 38, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-SOURCE'   , 39, 'Data Source'     , 'Data Source'     , 0, 0, 0, '', 0,   0, 0, '', 1, 39, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cb_report_01';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cb_report_01 Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????cb_report_01_wm.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Betsy
 日期 : 2017-11-21
 內容 : cb_report_01_wm
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cb_report_01_wm] (
	[date]          	DATE NOT NULL,
	[seq]           	INT NOT NULL,
	[cname]         	NVARCHAR(80) NOT NULL,
	[ename]         	VARCHAR(80) NOT NULL,
	[source]        	CHAR(1) NOT NULL,
	[note]          	VARCHAR(100) NOT NULL,
	[exch_rate]     	NUMERIC(11,8) NOT NULL,
	[total_amt]     	NUMERIC(20,5) NOT NULL,
	[forward_settle]	VARCHAR(3) NOT NULL,
	[JOB-CODE]      	CHAR(1) NOT NULL,
	[CURR]          	CHAR(3) NOT NULL,
	[BANK]          	CHAR(4) NOT NULL,
	[SER-NO]        	CHAR(5) NOT NULL,
	[REM-TYPE]      	CHAR(1) NOT NULL,
	[OP-DATE]       	CHAR(8) NOT NULL,
	[DATA-NO]       	CHAR(12) NOT NULL,
	[BAN-IDNO]      	CHAR(10) NOT NULL,
	[BIRTH-DATE]    	CHAR(8) NOT NULL,
	[ISSUE-DATE]    	CHAR(8) NOT NULL,
	[EXP-DATE]      	CHAR(8) NOT NULL,
	[KIND-CODE]     	CHAR(1) NOT NULL,
	[DATA-KIND]     	CHAR(1) NOT NULL,
	[DATA-AMT-SIGN] 	CHAR(1) NOT NULL,
	[DATA-AMT]      	CHAR(14) NOT NULL,
	[FORWARD-SPL]   	CHAR(1) NOT NULL,
	[CLASS]         	CHAR(3) NOT NULL,
	[TOP]           	CHAR(1) NOT NULL,
	[690-SUB-CODE]  	CHAR(1) NOT NULL,
	[CNTRY]         	CHAR(2) NOT NULL,
	[NO-REP-FLAG]   	CHAR(1) NOT NULL,
	[Q-ID]          	CHAR(2) NOT NULL,
	[NATURAL]       	CHAR(1) NOT NULL,
	[APROV-NO-FLAG] 	CHAR(1) NOT NULL,
	[SPEC-BANK]     	CHAR(4) NOT NULL,
	[DOCU-NO]       	CHAR(7) NOT NULL,
	[NT-EXCHG-RATE] 	CHAR(11) NOT NULL,
	[OPPO-NAME]     	CHAR(40) NOT NULL,
	[SWIFT-BANK]    	CHAR(11) NOT NULL,
	[OPPO-BANK]     	CHAR(60) NOT NULL,
	[DATA-SOURCE]   	CHAR(1) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_01_wm]') AND type in (N'U'))
	EXEC sp_backup_data 'cb_report_01_wm', 'Tmp_cb_report_01_wm'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_01_wm]') AND type in (N'U'))
	DROP TABLE cb_report_01_wm;	
	
EXEC sp_rename 'Tmp_cb_report_01_wm', 'cb_report_01_wm', 'OBJECT'
GO	

ALTER TABLE [dbo].[cb_report_01_wm] ADD CONSTRAINT [PK_cb_report_01_wm] PRIMARY KEY CLUSTERED
(
	[date],[seq]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cb_report_01_wm', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cb_report_01_wm', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '(財管)外匯收入資料傳輸檔案格式';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'date'          ,  1, 'Date'            , 'Date'            , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'seq'           ,  2, 'Sequence No'     , 'Sequence No'     , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname'         ,  3, 'Chinese Name'    , 'Chinese Name'    , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ename'         ,  4, 'English Name'    , 'English Name'    , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source'        ,  5, 'Source'          , 'Source'          , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'          ,  6, 'Remark'          , 'Remark'          , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'exch_rate'     ,  7, 'Rate'            , 'Rate'            , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'total_amt'     ,  8, 'Total Amount'    , 'Total Amount'    , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'forward_settle',  9, 'Forward Settle'  , 'Forward Settle'  , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'JOB-CODE'      , 10, 'Job Code'        , 'Job Code'        , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CURR'          , 11, 'Ccy'             , 'Ccy'             , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BANK'          , 12, 'Bank'            , 'Bank'            , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SER-NO'        , 13, 'Ser No'          , 'Ser No'          , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'REM-TYPE'      , 14, 'Rem Type'        , 'Rem Type'        , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OP-DATE'       , 15, 'Op Date'         , 'Op Date'         , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-NO'       , 16, 'Data No'         , 'Data No'         , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BAN-IDNO'      , 17, 'Ban Idno'        , 'Ban Idno'        , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BIRTH-DATE'    , 18, 'Birth Date'      , 'Birth Date'      , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ISSUE-DATE'    , 19, 'Issue Date'      , 'Issue Date'      , 0, 0, 0, '', 0,   0, 0, '', 1, 19, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'EXP-DATE'      , 20, 'Expire Date'     , 'Expire Date'     , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'KIND-CODE'     , 21, 'Kind Code'       , 'Kind Code'       , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-KIND'     , 22, 'Data Kind'       , 'Data Kind'       , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-AMT-SIGN' , 23, 'Data Amt Sign'   , 'Data Amt Sign'   , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-AMT'      , 24, 'Data Amount'     , 'Data Amount'     , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'FORWARD-SPL'   , 25, 'Forward Spl'     , 'Forward Spl'     , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CLASS'         , 26, 'Class'           , 'Class'           , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'TOP'           , 27, 'Top'             , 'Top'             , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, '690-SUB-CODE'  , 28, 'Sub Code'        , 'Sub Code'        , 0, 0, 0, '', 0,   0, 0, '', 1, 28, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CNTRY'         , 29, 'Cntry'           , 'Cntry'           , 0, 0, 0, '', 0,   0, 0, '', 1, 29, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NO-REP-FLAG'   , 30, 'No Rep Flag'     , 'No Rep Flag'     , 0, 0, 0, '', 0,   0, 0, '', 1, 30, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'Q-ID'          , 31, 'Q Id'            , 'Q Id'            , 0, 0, 0, '', 0,   0, 0, '', 1, 31, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NATURAL'       , 32, 'Natural'         , 'Natural'         , 0, 0, 0, '', 0,   0, 0, '', 1, 32, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'APROV-NO-FLAG' , 33, 'Approval No Flag', 'Approval No Flag', 0, 0, 0, '', 0,   0, 0, '', 1, 33, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SPEC-BANK'     , 34, 'Spec Bank'       , 'Spec Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 34, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DOCU-NO'       , 35, 'Docu No'         , 'Docu No'         , 0, 0, 0, '', 0,   0, 0, '', 1, 35, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NT-EXCHG-RATE' , 36, 'Nt Exchg Rate'   , 'Nt Exchg Rate'   , 0, 0, 0, '', 0,   0, 0, '', 1, 36, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OPPO-NAME'     , 37, 'Oppo Name'       , 'Oppo Name'       , 0, 0, 0, '', 0,   0, 0, '', 1, 37, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SWIFT-BANK'    , 38, 'Swift Bank'      , 'Swift Bank'      , 0, 0, 0, '', 0,   0, 0, '', 1, 38, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OPPO-BANK'     , 39, 'Oppo Bank'       , 'Oppo Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 39, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-SOURCE'   , 40, 'Data Source'     , 'Data Source'     , 0, 0, 0, '', 0,   0, 0, '', 1, 40, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cb_report_01_wm';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cb_report_01_wm Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????cb_report_02.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Betsy
 日期 : 2017-11-21
 內容 : cb_report_02
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cb_report_02] (
	[pno]           	INT NOT NULL,
	[date]          	DATE NOT NULL,
	[seq]           	INT NOT NULL,
	[source]        	VARCHAR(3) NOT NULL,
	[note]          	VARCHAR(100) NOT NULL,
	[exch_rate]     	NUMERIC(11,8) NOT NULL,
	[total_amt]     	NUMERIC(20,5) NOT NULL,
	[forward_settle]	VARCHAR(3) NOT NULL,
	[JOB-CODE]      	CHAR(1) NOT NULL,
	[CURR]          	CHAR(3) NOT NULL,
	[BANK]          	CHAR(4) NOT NULL,
	[SER-NO]        	CHAR(5) NOT NULL,
	[REM-TYPE]      	CHAR(1) NOT NULL,
	[OP-DATE]       	CHAR(8) NOT NULL,
	[DATA-NO]       	CHAR(12) NOT NULL,
	[BAN-IDNO]      	CHAR(10) NOT NULL,
	[BIRTH-DATE]    	CHAR(8) NOT NULL,
	[ISSUE-DATE]    	CHAR(8) NOT NULL,
	[EXP-DATE]      	CHAR(8) NOT NULL,
	[KIND-CODE]     	CHAR(1) NOT NULL,
	[DATA-KIND]     	CHAR(1) NOT NULL,
	[DATA-AMT-SIGN] 	CHAR(1) NOT NULL,
	[DATA-AMT]      	CHAR(14) NOT NULL,
	[FORWARD-SPL]   	CHAR(1) NOT NULL,
	[CLASS]         	CHAR(3) NOT NULL,
	[TOP]           	CHAR(1) NOT NULL,
	[690-SUB-CODE]  	CHAR(1) NOT NULL,
	[CNTRY]         	CHAR(2) NOT NULL,
	[NO-REP-FLAG]   	CHAR(1) NOT NULL,
	[Q-ID]          	CHAR(2) NOT NULL,
	[NATURAL]       	CHAR(1) NOT NULL,
	[APROV-NO-FLAG] 	CHAR(1) NOT NULL,
	[SPEC-BANK]     	CHAR(4) NOT NULL,
	[DOCU-NO]       	CHAR(7) NOT NULL,
	[NT-EXCHG-RATE] 	CHAR(11) NOT NULL,
	[OPPO-NAME]     	CHAR(40) NOT NULL,
	[SWIFT-BANK]    	CHAR(11) NOT NULL,
	[OPPO-BANK]     	CHAR(60) NOT NULL,
	[ACCOUNT-NO]    	CHAR(20) NOT NULL,
	[DATA-SOURCE]   	CHAR(1) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_02]') AND type in (N'U'))
	EXEC sp_backup_data 'cb_report_02', 'Tmp_cb_report_02'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_02]') AND type in (N'U'))
	DROP TABLE cb_report_02;	
	
EXEC sp_rename 'Tmp_cb_report_02', 'cb_report_02', 'OBJECT'
GO	

ALTER TABLE [dbo].[cb_report_02] ADD CONSTRAINT [PK_cb_report_02] PRIMARY KEY CLUSTERED
(
	[pno],[date],[seq]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cb_report_02', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cb_report_02', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '外匯支出資料傳輸檔案格式';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'pno'           ,  1, 'Pno'             , 'Pno'             , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date'          ,  2, 'Date'            , 'Date'            , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'seq'           ,  3, 'Sequence No'     , 'Sequence No'     , 1, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source'        ,  4, 'Source'          , 'Source'          , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'          ,  5, 'Remark'          , 'Remark'          , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'exch_rate'     ,  6, 'Rate'            , 'Rate'            , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'total_amt'     ,  7, 'Total Amount'    , 'Total Amount'    , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'forward_settle',  8, 'Forward Settle'  , 'Forward Settle'  , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'JOB-CODE'      ,  9, 'Job Code'        , 'Job Code'        , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CURR'          , 10, 'Ccy'             , 'Ccy'             , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BANK'          , 11, 'Bank'            , 'Bank'            , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SER-NO'        , 12, 'Ser No'          , 'Ser No'          , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'REM-TYPE'      , 13, 'Rem Type'        , 'Rem Type'        , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OP-DATE'       , 14, 'Op Date'         , 'Op Date'         , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-NO'       , 15, 'Data No'         , 'Data No'         , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BAN-IDNO'      , 16, 'Ban Idno'        , 'Ban Idno'        , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BIRTH-DATE'    , 17, 'Birth Date'      , 'Birth Date'      , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ISSUE-DATE'    , 18, 'Issue Date'      , 'Issue Date'      , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'EXP-DATE'      , 19, 'Expire Date'     , 'Expire Date'     , 0, 0, 0, '', 0,   0, 0, '', 1, 19, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'KIND-CODE'     , 20, 'Kind Code'       , 'Kind Code'       , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-KIND'     , 21, 'Data Kind'       , 'Data Kind'       , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-AMT-SIGN' , 22, 'Data Amt Sign'   , 'Data Amt Sign'   , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-AMT'      , 23, 'Data Amount'     , 'Data Amount'     , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'FORWARD-SPL'   , 24, 'Forward Spl'     , 'Forward Spl'     , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CLASS'         , 25, 'Class'           , 'Class'           , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'TOP'           , 26, 'Top'             , 'Top'             , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, '690-SUB-CODE'  , 27, 'Sub Code'        , 'Sub Code'        , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CNTRY'         , 28, 'Cntry'           , 'Cntry'           , 0, 0, 0, '', 0,   0, 0, '', 1, 28, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NO-REP-FLAG'   , 29, 'No Rep Flag'     , 'No Rep Flag'     , 0, 0, 0, '', 0,   0, 0, '', 1, 29, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'Q-ID'          , 30, 'Q Id'            , 'Q Id'            , 0, 0, 0, '', 0,   0, 0, '', 1, 30, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NATURAL'       , 31, 'Natural'         , 'Natural'         , 0, 0, 0, '', 0,   0, 0, '', 1, 31, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'APROV-NO-FLAG' , 32, 'Approval No Flag', 'Approval No Flag', 0, 0, 0, '', 0,   0, 0, '', 1, 32, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SPEC-BANK'     , 33, 'Spec Bank'       , 'Spec Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 33, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DOCU-NO'       , 34, 'Docu No'         , 'Docu No'         , 0, 0, 0, '', 0,   0, 0, '', 1, 34, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NT-EXCHG-RATE' , 35, 'Nt Exchg Rate'   , 'Nt Exchg Rate'   , 0, 0, 0, '', 0,   0, 0, '', 1, 35, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OPPO-NAME'     , 36, 'Oppo Name'       , 'Oppo Name'       , 0, 0, 0, '', 0,   0, 0, '', 1, 36, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SWIFT-BANK'    , 37, 'Swift Bank'      , 'Swift Bank'      , 0, 0, 0, '', 0,   0, 0, '', 1, 37, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OPPO-BANK'     , 38, 'Oppo Bank'       , 'Oppo Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 38, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ACCOUNT-NO'    , 39, 'Account No'      , 'Account No'      , 0, 0, 0, '', 0,   0, 0, '', 1, 39, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-SOURCE'   , 40, 'Data Source'     , 'Data Source'     , 0, 0, 0, '', 0,   0, 0, '', 1, 40, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cb_report_02';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cb_report_02 Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????cb_report_02_wm.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Betsy
 日期 : 2017-11-21
 內容 : cb_report_02_wm
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cb_report_02_wm] (
	[date]          	DATE NOT NULL,
	[seq]           	INT NOT NULL,
	[cname]         	NVARCHAR(80) NOT NULL,
	[ename]         	VARCHAR(80) NOT NULL,
	[source]        	VARCHAR(3) NOT NULL,
	[note]          	VARCHAR(100) NOT NULL,
	[exch_rate]     	NUMERIC(11,8) NOT NULL,
	[total_amt]     	NUMERIC(20,5) NOT NULL,
	[forward_settle]	VARCHAR(3) NOT NULL,
	[JOB-CODE]      	CHAR(1) NOT NULL,
	[CURR]          	CHAR(3) NOT NULL,
	[BANK]          	CHAR(4) NOT NULL,
	[SER-NO]        	CHAR(5) NOT NULL,
	[REM-TYPE]      	CHAR(1) NOT NULL,
	[OP-DATE]       	CHAR(8) NOT NULL,
	[DATA-NO]       	CHAR(12) NOT NULL,
	[BAN-IDNO]      	CHAR(10) NOT NULL,
	[BIRTH-DATE]    	CHAR(8) NOT NULL,
	[ISSUE-DATE]    	CHAR(8) NOT NULL,
	[EXP-DATE]      	CHAR(8) NOT NULL,
	[KIND-CODE]     	CHAR(1) NOT NULL,
	[DATA-KIND]     	CHAR(1) NOT NULL,
	[DATA-AMT-SIGN] 	CHAR(1) NOT NULL,
	[DATA-AMT]      	CHAR(14) NOT NULL,
	[FORWARD-SPL]   	CHAR(1) NOT NULL,
	[CLASS]         	CHAR(3) NOT NULL,
	[TOP]           	CHAR(1) NOT NULL,
	[690-SUB-CODE]  	CHAR(1) NOT NULL,
	[CNTRY]         	CHAR(2) NOT NULL,
	[NO-REP-FLAG]   	CHAR(1) NOT NULL,
	[Q-ID]          	CHAR(2) NOT NULL,
	[NATURAL]       	CHAR(1) NOT NULL,
	[APROV-NO-FLAG] 	CHAR(1) NOT NULL,
	[SPEC-BANK]     	CHAR(4) NOT NULL,
	[DOCU-NO]       	CHAR(7) NOT NULL,
	[NT-EXCHG-RATE] 	CHAR(11) NOT NULL,
	[OPPO-NAME]     	CHAR(40) NOT NULL,
	[SWIFT-BANK]    	CHAR(11) NOT NULL,
	[OPPO-BANK]     	CHAR(60) NOT NULL,
	[ACCOUNT-NO]    	CHAR(20) NOT NULL,
	[DATA-SOURCE]   	CHAR(1) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_02_wm]') AND type in (N'U'))
	EXEC sp_backup_data 'cb_report_02_wm', 'Tmp_cb_report_02_wm'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_02_wm]') AND type in (N'U'))
	DROP TABLE cb_report_02_wm;	
	
EXEC sp_rename 'Tmp_cb_report_02_wm', 'cb_report_02_wm', 'OBJECT'
GO	

ALTER TABLE [dbo].[cb_report_02_wm] ADD CONSTRAINT [PK_cb_report_02_wm] PRIMARY KEY CLUSTERED
(
	[date],[seq]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cb_report_02_wm', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cb_report_02_wm', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '(財管)外匯支出資料傳輸檔案格式';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'date'          ,  1, 'Date'            , 'Date'            , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'seq'           ,  2, 'Sequence No'     , 'Sequence No'     , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname'         ,  3, 'Chinese Name'    , 'Chinese Name'    , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ename'         ,  4, 'English Name'    , 'English Name'    , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source'        ,  5, 'Source'          , 'Source'          , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'          ,  6, 'Remark'          , 'Remark'          , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'exch_rate'     ,  7, 'Rate'            , 'Rate'            , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'total_amt'     ,  8, 'Total Amount'    , 'Total Amount'    , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'forward_settle',  9, 'Forward Settle'  , 'Forward Settle'  , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'JOB-CODE'      , 10, 'Job Code'        , 'Job Code'        , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CURR'          , 11, 'Ccy'             , 'Ccy'             , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BANK'          , 12, 'Bank'            , 'Bank'            , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SER-NO'        , 13, 'Ser No'          , 'Ser No'          , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'REM-TYPE'      , 14, 'Rem Type'        , 'Rem Type'        , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OP-DATE'       , 15, 'Op Date'         , 'Op Date'         , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-NO'       , 16, 'Data No'         , 'Data No'         , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BAN-IDNO'      , 17, 'Ban Idno'        , 'Ban Idno'        , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BIRTH-DATE'    , 18, 'Birth Date'      , 'Birth Date'      , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ISSUE-DATE'    , 19, 'Issue Date'      , 'Issue Date'      , 0, 0, 0, '', 0,   0, 0, '', 1, 19, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'EXP-DATE'      , 20, 'Expire Date'     , 'Expire Date'     , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'KIND-CODE'     , 21, 'Kind Code'       , 'Kind Code'       , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-KIND'     , 22, 'Data Kind'       , 'Data Kind'       , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-AMT-SIGN' , 23, 'Data Amt Sign'   , 'Data Amt Sign'   , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-AMT'      , 24, 'Data Amount'     , 'Data Amount'     , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'FORWARD-SPL'   , 25, 'Forward Spl'     , 'Forward Spl'     , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CLASS'         , 26, 'Class'           , 'Class'           , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'TOP'           , 27, 'Top'             , 'Top'             , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, '690-SUB-CODE'  , 28, 'Sub Code'        , 'Sub Code'        , 0, 0, 0, '', 0,   0, 0, '', 1, 28, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CNTRY'         , 29, 'Cntry'           , 'Cntry'           , 0, 0, 0, '', 0,   0, 0, '', 1, 29, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NO-REP-FLAG'   , 30, 'No Rep Flag'     , 'No Rep Flag'     , 0, 0, 0, '', 0,   0, 0, '', 1, 30, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'Q-ID'          , 31, 'Q Id'            , 'Q Id'            , 0, 0, 0, '', 0,   0, 0, '', 1, 31, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NATURAL'       , 32, 'Natural'         , 'Natural'         , 0, 0, 0, '', 0,   0, 0, '', 1, 32, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'APROV-NO-FLAG' , 33, 'Approval No Flag', 'Approval No Flag', 0, 0, 0, '', 0,   0, 0, '', 1, 33, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SPEC-BANK'     , 34, 'Spec Bank'       , 'Spec Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 34, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DOCU-NO'       , 35, 'Docu No'         , 'Docu No'         , 0, 0, 0, '', 0,   0, 0, '', 1, 35, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NT-EXCHG-RATE' , 36, 'Nt Exchg Rate'   , 'Nt Exchg Rate'   , 0, 0, 0, '', 0,   0, 0, '', 1, 36, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OPPO-NAME'     , 37, 'Oppo Name'       , 'Oppo Name'       , 0, 0, 0, '', 0,   0, 0, '', 1, 37, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'SWIFT-BANK'    , 38, 'Swift Bank'      , 'Swift Bank'      , 0, 0, 0, '', 0,   0, 0, '', 1, 38, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'OPPO-BANK'     , 39, 'Oppo Bank'       , 'Oppo Bank'       , 0, 0, 0, '', 0,   0, 0, '', 1, 39, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ACCOUNT-NO'    , 40, 'Account No'      , 'Account No'      , 0, 0, 0, '', 0,   0, 0, '', 1, 40, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-SOURCE'   , 41, 'Data Source'     , 'Data Source'     , 0, 0, 0, '', 0,   0, 0, '', 1, 41, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cb_report_02_wm';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cb_report_02_wm Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????cb_report_03.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Betsy
 日期 : 2017-11-09
 內容 : cb_report_03
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cb_report_03] (
	[date]        	DATE NOT NULL,
	[seq]         	INT NOT NULL,
	[type]        	SMALLINT NOT NULL,
	[note]        	VARCHAR(100) NOT NULL,
	[DATA-DATE]   	CHAR(8) NOT NULL,
	[BANK]        	CHAR(2) NOT NULL,
	[E-I-CODE]    	CHAR(1) NOT NULL,
	[CURR]        	CHAR(3) NOT NULL,
	[ITEM]        	CHAR(2) NOT NULL,
	[EXCHG-NORM]  	CHAR(14) NOT NULL,
	[EXCHG-CORR]  	CHAR(14) NOT NULL,
	[STORE-FORE-N]	CHAR(14) NOT NULL,
	[STORE-FORE-C]	CHAR(14) NOT NULL,
	[NO-EXCHG-O-N]	CHAR(14) NOT NULL,
	[NO-EXCHG-O-C]	CHAR(14) NOT NULL,
	[LINE-TOT-N]  	CHAR(14) NOT NULL,
	[LINE-TOT-C]  	CHAR(14) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_03]') AND type in (N'U'))
	EXEC sp_backup_data 'cb_report_03', 'Tmp_cb_report_03'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_03]') AND type in (N'U'))
	DROP TABLE cb_report_03;	
	
EXEC sp_rename 'Tmp_cb_report_03', 'cb_report_03', 'OBJECT'
GO	

ALTER TABLE [dbo].[cb_report_03] ADD CONSTRAINT [PK_cb_report_03] PRIMARY KEY CLUSTERED
(
	[date],[seq],[type]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cb_report_03', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cb_report_03', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '外匯交易日報資料傳輸檔案格式';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'date'        ,  1, '日期'                           , '日期'                           , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'seq'         ,  2, '序號'                           , '序號'                           , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'type'        ,  3, '業務類別'                       , '業務類別'                       , 1, 1, 0, '', 0,  -1, 0, '', 1,  3, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'        ,  4, '備註'                           , '備註'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-DATE'   ,  5, '交易資料日期'                   , '交易資料日期'                   , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BANK'        ,  6, '證券商'                         , '證券商'                         , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'E-I-CODE'    ,  7, '外匯收入/支出別'                , '外匯收入/支出別'                , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CURR'        ,  8, '幣別'                           , '幣別'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ITEM'        ,  9, '類別'                           , '類別'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'EXCHG-NORM'  , 10, 'N/A'                            , 'N/A'                            , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'EXCHG-CORR'  , 11, 'N/A'                            , 'N/A'                            , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'STORE-FORE-N', 12, '外匯保管/信託帳戶存入/支付-正常', '外匯保管/信託帳戶存入/支付-正常', 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'STORE-FORE-C', 13, '外匯保管/信託帳戶存入/支付-調整', '外匯保管/信託帳戶存入/支付-調整', 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NO-EXCHG-O-N', 14, '其他─正常'                      , '其他─正常'                      , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NO-EXCHG-O-C', 15, '其他─調整'                      , '其他─調整'                      , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'LINE-TOT-N'  , 16, '各列合計─正常'                  , '各列合計─正常'                  , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'LINE-TOT-C'  , 17, '各列合計─調整'                  , '各列合計─調整'                  , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cb_report_03';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cb_report_03 Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????cb_report_03_wm.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Yuan
 日期 : 2017-11-09
 內容 : cb_report_03_wm
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_cb_report_03_wm] (
	[date]        	DATE NOT NULL,
	[seq]         	INT NOT NULL,
	[note]        	VARCHAR(100) NOT NULL,
	[DATA-DATE]   	CHAR(8) NOT NULL,
	[BANK]        	CHAR(2) NOT NULL,
	[E-I-CODE]    	CHAR(1) NOT NULL,
	[CURR]        	CHAR(3) NOT NULL,
	[ITEM]        	CHAR(2) NOT NULL,
	[EXCHG-NORM]  	CHAR(14) NOT NULL,
	[EXCHG-CORR]  	CHAR(14) NOT NULL,
	[STORE-FORE-N]	CHAR(14) NOT NULL,
	[STORE-FORE-C]	CHAR(14) NOT NULL,
	[NO-EXCHG-O-N]	CHAR(14) NOT NULL,
	[NO-EXCHG-O-C]	CHAR(14) NOT NULL,
	[LINE-TOT-N]  	CHAR(14) NOT NULL,
	[LINE-TOT-C]  	CHAR(14) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_03_wm]') AND type in (N'U'))
	EXEC sp_backup_data 'cb_report_03_wm', 'Tmp_cb_report_03_wm'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[cb_report_03_wm]') AND type in (N'U'))
	DROP TABLE cb_report_03_wm;	
	
EXEC sp_rename 'Tmp_cb_report_03_wm', 'cb_report_03_wm', 'OBJECT'
GO	

ALTER TABLE [dbo].[cb_report_03_wm] ADD CONSTRAINT [PK_cb_report_03_wm] PRIMARY KEY CLUSTERED
(
	[date],[seq]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'cb_report_03_wm', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'cb_report_03_wm', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '(財管)外匯交易日報資料傳輸檔案格式';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'date'        ,  1, '日期'                           , '日期'                           , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'seq'         ,  2, '序號'                           , '序號'                           , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'        ,  3, '備註'                           , '備註'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'DATA-DATE'   ,  4, '交易資料日期'                   , '交易資料日期'                   , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'BANK'        ,  5, '證券商'                         , '證券商'                         , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'E-I-CODE'    ,  6, '外匯收入/支出別'                , '外匯收入/支出別'                , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'CURR'        ,  7, '幣別'                           , '幣別'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ITEM'        ,  8, '類別'                           , '類別'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'EXCHG-NORM'  ,  9, 'N/A'                            , 'N/A'                            , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'EXCHG-CORR'  , 10, 'N/A'                            , 'N/A'                            , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'STORE-FORE-N', 11, '外匯保管/信託帳戶存入/支付-正常', '外匯保管/信託帳戶存入/支付-正常', 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'STORE-FORE-C', 12, '外匯保管/信託帳戶存入/支付-調整', '外匯保管/信託帳戶存入/支付-調整', 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NO-EXCHG-O-N', 13, '其他─正常'                      , '其他─正常'                      , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'NO-EXCHG-O-C', 14, '其他─調整'                      , '其他─調整'                      , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'LINE-TOT-N'  , 15, '各列合計─正常'                  , '各列合計─正常'                  , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'LINE-TOT-C'  , 16, '各列合計─調整'                  , '各列合計─調整'                  , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'cb_report_03_wm';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table cb_report_03_wm Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????fx_balance_opt.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Yvonne
 日期 : 2015-05-01
 內容 : fx_balance_opt
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_fx_balance_opt] (
	[type]      	SMALLINT NOT NULL,
	[trade_type]	SMALLINT NOT NULL,
	[code]      	VARCHAR(3) NOT NULL,
	[item]      	NVARCHAR(50) NOT NULL,
	[note]      	NVARCHAR(500) NOT NULL,
	[loguser]   	VARCHAR(20) NOT NULL,
	[logtime]   	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[fx_balance_opt]') AND type in (N'U'))
	EXEC sp_backup_data 'fx_balance_opt', 'Tmp_fx_balance_opt'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[fx_balance_opt]') AND type in (N'U'))
	DROP TABLE fx_balance_opt;

EXEC sp_rename 'Tmp_fx_balance_opt', 'fx_balance_opt', 'OBJECT'
GO

ALTER TABLE [dbo].[fx_balance_opt] ADD CONSTRAINT [PK_fx_balance_opt] PRIMARY KEY CLUSTERED
(
	[type],[trade_type],[code]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'fx_balance_opt', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'fx_balance_opt', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '外匯申報選項';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'type'      ,  1, '外匯申報選項', '外匯申報選項', 1, 1, 0, '', 0, 165, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_type',  2, '交易型態'    , '交易型態'    , 1, 1, 0, '', 0,   0, 0, '', 1, 2, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'code'      ,  3, '分類編號'    , '分類編號'    , 1, 1, 0, '', 0,   0, 0, '', 1, 3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'item'      ,  4, '項目'        , '項目'        , 0, 0, 0, '', 0,   0, 0, '', 1, 4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'      ,  5, '說明'        , '說明'        , 0, 0, 0, '', 0,   0, 0, '', 1, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'   ,  6, '異動人員'    , '異動人員'    , 0, 0, 0, '', 0,   0, 0, '', 0, 6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'   ,  7, '異動時間'    , '異動時間'    , 0, 0, 0, '', 0,   0, 0, '', 0, 7, 150, 'DateEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'fx_balance_opt';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table fx_balance_opt Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????fx_balance_opt_list.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Frank
 日期 : 2015-04-07
 內容 : fx_balance_opt_list
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_fx_balance_opt_list] (
	[trade_type]	SMALLINT NOT NULL,
	[code]      	VARCHAR(3) NOT NULL,
	[list_item] 	VARCHAR(3) NOT NULL,
	[note]      	NVARCHAR(500) NOT NULL,
	[loguser]   	VARCHAR(20) NOT NULL,
	[logtime]   	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[fx_balance_opt_list]') AND type in (N'U'))
	EXEC sp_backup_data 'fx_balance_opt_list', 'Tmp_fx_balance_opt_list'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[fx_balance_opt_list]') AND type in (N'U'))
	DROP TABLE fx_balance_opt_list;	
	
EXEC sp_rename 'Tmp_fx_balance_opt_list', 'fx_balance_opt_list', 'OBJECT'
GO	

ALTER TABLE [dbo].[fx_balance_opt_list] ADD CONSTRAINT [PK_fx_balance_opt_list] PRIMARY KEY CLUSTERED
(
	[trade_type],[code],[list_item]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'fx_balance_opt_list', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'fx_balance_opt_list', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '外匯收支分類細項';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'trade_type',  1, '交易型態', '交易型態', 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'code'      ,  2, '分類編號', '分類編號', 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'list_item' ,  3, '細項代號', '細項代號', 1, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'note'      ,  4, '說明'    , '說明'    , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'   ,  5, '異動人員', '異動人員', 0, 0, 0, '', 0,   0, 0, '', 0,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'   ,  6, '異動時間', '異動時間', 0, 0, 0, '', 0,   0, 0, '', 0,  6, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'fx_balance_opt_list';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table fx_balance_opt_list Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_account.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-02
 內容 : afos_client_account
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_account] (
	[code]          CHAR(10) NOT NULL,
	[lno]       	INT NOT NULL,
	[broker]    	VARCHAR(12) NOT NULL,
	[acc_number]	VARCHAR(16) NOT NULL,
	[acc_name]  	NVARCHAR(76) NOT NULL,
	[loguser]   	VARCHAR(20) NOT NULL,
	[logtime]   	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_account]') AND type in (N'U'))
	EXEC sp_backup_data 'afos_client_account', 'Tmp_afos_client_account'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_account]') AND type in (N'U'))
	DROP TABLE afos_client_account;	
	
EXEC sp_rename 'Tmp_afos_client_account', 'afos_client_account', 'OBJECT'
GO	

ALTER TABLE [dbo].[afos_client_account] ADD CONSTRAINT [PK_afos_client_account] PRIMARY KEY CLUSTERED
(
	[code]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'afos_client_account', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_account', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Account';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'lno'       ,  1, 'lno'           , 'lno'             , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'code'      ,  2, '帳戶內碼'        , '帳戶內碼'         , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'broker'    ,  2, 'Bank Code(Full)', 'Bank Code(Full)', 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc_number',  3, 'Account Number' , 'Account Number' , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc_name'  ,  4, 'Account Name'   , 'Account Name'   , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'   ,  5, 'Loguser'        , 'Loguser'        , 0, 0, 0, '', 0,   0, 0, '', 0,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'   ,  6, 'Logtime'        , 'Logtime'        , 0, 0, 0, '', 0,   0, 0, '', 0,  6, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_account';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_account Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_chop.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-02
 內容 : afos_client_chop
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_chop] (
	[lno]        	INT NOT NULL,
	[date]       	DATE NOT NULL,
	[type]       	SMALLINT NOT NULL,
	[file_name]  	NVARCHAR(200) NOT NULL,
	[verify_code]	VARBINARY(MAX) NOT NULL,
	[lock]       	BIT NOT NULL,
	[lockuser]   	VARCHAR(20) NOT NULL,
	[locktime]   	DATETIME NOT NULL,
	[loguser]    	VARCHAR(20) NOT NULL,
	[logtime]    	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_chop]') AND type in (N'U'))
	EXEC sp_backup_data 'afos_client_chop', 'Tmp_afos_client_chop'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_chop]') AND type in (N'U'))
	DROP TABLE afos_client_chop;	
	
EXEC sp_rename 'Tmp_afos_client_chop', 'afos_client_chop', 'OBJECT'
GO	

ALTER TABLE [dbo].[afos_client_chop] ADD CONSTRAINT [PK_afos_client_chop] PRIMARY KEY CLUSTERED
(
	[lno], [date]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'afos_client_chop', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_chop', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Chop/Sign';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'lno'        ,  1, 'Local No'   , 'Local No'   , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date'       ,  2, 'Date'       , 'Date'       , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'type'       ,  3, 'File Type'  , 'File Type'  , 0, 1, 0, '', 0, 504, 0, '', 1,  3, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'file_name'  ,  4, 'File Name'  , 'File Name'  , 0, 1, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'verify_code',  6, 'Verify Code', 'Verify Code', 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lock'       ,  7, 'Lock'       , 'Lock'       , 0, 0, 0, '', 0,   0, 0, '', 0,  7, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lockuser'   ,  8, 'Lockuser'   , 'Lockuser'   , 0, 0, 0, '', 0,   0, 0, '', 0,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'locktime'   ,  9, 'Locktime'   , 'Locktime'   , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'    , 10, 'Loguser'    , 'Loguser'    , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'    , 11, 'Logtime'    , 'Logtime'    , 0, 0, 0, '', 0,   0, 0, '', 0, 11, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_chop';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_chop Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_contact.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-02
 內容 : afos_client_contact
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_contact] (
	[code]          CHAR(10) NOT NULL,
	[lno]         	INT NOT NULL,
	[contact_type]	SMALLINT NOT NULL,
	[contact]     	NVARCHAR(50) NOT NULL,
	[phone]       	VARCHAR(20) NOT NULL,
	[fax]         	VARCHAR(20) NOT NULL,
	[is_for_fax]  	BIT NOT NULL,
	[email]       	VARCHAR(100) NOT NULL,
	[is_for_email]	BIT NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_contact]') AND type in (N'U'))
	EXEC sp_backup_data 'afos_client_contact', 'Tmp_afos_client_contact'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_contact]') AND type in (N'U'))
	DROP TABLE afos_client_contact;	
	
EXEC sp_rename 'Tmp_afos_client_contact', 'afos_client_contact', 'OBJECT'
GO	

ALTER TABLE [dbo].[afos_client_contact] ADD CONSTRAINT [PK_afos_client_contact] PRIMARY KEY CLUSTERED
(
	[code]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'afos_client_contact', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_contact', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Contact';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'code'        ,  4, '聯絡人內碼'                  , '聯絡人內碼'                , 1, 1, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lno'         ,  1, 'lno'                       , 'lno'                       , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'contact_type',  2, 'Contact Type'              , 'Contact Type'              , 0, 1, 0, '', 0, 505, 0, '', 1,  2, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'contact'     ,  3, 'Contact'                   , 'Contact'                   , 0, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'phone'       ,  4, 'Phone Number'              , 'Phone Number'              , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fax'         ,  5, 'Fax Number'                , 'Fax Number'                , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_for_fax'  ,  6, 'Confirmation To This Fax'  , 'Confirmation To This Fax'  , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'email'       ,  7, 'Email'                     , 'Emai'                      , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_for_email',  8, 'Confirmation To This Email', 'Confirmation To This Email', 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  9, 'Loguser'                   , 'Loguser'                   , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     , 10, 'Logtime'                   , 'Logtime'                   , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_contact';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_contact Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_contact_edit.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-02
 內容 : afos_client_contact_edit
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_contact_edit] (
	[code]          CHAR(10) NOT NULL,
	[lno]         	INT NOT NULL,
	[contact_type]	SMALLINT NOT NULL,
	[contact]     	NVARCHAR(50) NOT NULL,
	[phone]       	VARCHAR(20) NOT NULL,
	[fax]         	VARCHAR(20) NOT NULL,
	[is_for_fax]  	BIT NOT NULL,
	[email]       	VARCHAR(100) NOT NULL,
	[is_for_email]	BIT NOT NULL,
	[loguser]     	VARCHAR(20) NOT NULL,
	[logtime]     	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_contact_edit]') AND type in (N'U'))
	EXEC sp_backup_data 'afos_client_contact_edit', 'Tmp_afos_client_contact_edit'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_contact_edit]') AND type in (N'U'))
	DROP TABLE afos_client_contact_edit;	
	
EXEC sp_rename 'Tmp_afos_client_contact_edit', 'afos_client_contact_edit', 'OBJECT'
GO	

ALTER TABLE [dbo].[afos_client_contact_edit] ADD CONSTRAINT [PK_afos_client_contact_edit] PRIMARY KEY CLUSTERED
(
	[code]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'afos_client_contact_edit', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_contact_edit', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Contact';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'code'        ,  4, '聯絡人內碼'                  , '聯絡人內碼'                , 1, 1, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lno'         ,  1, 'lno'                       , 'lno'                       , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'contact_type',  2, 'Contact Type'              , 'Contact Type'              , 0, 1, 0, '', 0, 505, 0, '', 1,  2, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'contact'     ,  3, 'Contact'                   , 'Contact'                   , 0, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'phone'       ,  4, 'Phone Number'              , 'Phone Number'              , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fax'         ,  5, 'Fax Number'                , 'Fax Number'                , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_for_fax'  ,  6, 'Confirmation To This Fax'  , 'Confirmation To This Fax'  , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'email'       ,  7, 'Email'                     , 'Emai'                      , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_for_email',  8, 'Confirmation To This Email', 'Confirmation To This Email', 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  9, 'Loguser'                   , 'Loguser'                   , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     , 10, 'Logtime'                   , 'Logtime'                   , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_contact_edit';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_contact_edit Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_contact_log.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-02
 內容 : afos_client_contact_log
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_contact_log] (
    [seq]             INT NOT NULL,
    [code]            CHAR(10) NOT NULL,
    [lno]             INT NOT NULL,
    [contact_type]    SMALLINT NOT NULL,
    [contact]         NVARCHAR(50) NOT NULL,
    [phone]           VARCHAR(20) NOT NULL,
    [fax]             VARCHAR(20) NOT NULL,
    [is_for_fax]      BIT NOT NULL,
    [email]           VARCHAR(100) NOT NULL,
    [is_for_email]    BIT NOT NULL,
    [loguser]         VARCHAR(20) NOT NULL,
    [logtime]         DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_contact_log]') AND type in (N'U'))
    EXEC sp_backup_data 'afos_client_contact_log', 'Tmp_afos_client_contact_log'
    
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_contact_log]') AND type in (N'U'))
    DROP TABLE afos_client_contact_log;    
    
EXEC sp_rename 'Tmp_afos_client_contact_log', 'afos_client_contact_log', 'OBJECT'
GO    

ALTER TABLE [dbo].[afos_client_contact_log] ADD CONSTRAINT [PK_afos_client_contact_log] PRIMARY KEY CLUSTERED
(
    [seq], [code]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'afos_client_contact_log', 'ALL';
    
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_contact_log', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Contact';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'seq'         ,  1, 'serial number'             , 'serial number'             , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'code'        ,  4, '聯絡人內碼'                  , '聯絡人內碼'                , 1, 1, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lno'         ,  2, 'lno'                       , 'lno'                       , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'contact_type',  3, 'Contact Type'              , 'Contact Type'              , 0, 0, 0, '', 0, 505, 0, '', 1,  3, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'contact'     ,  4, 'Contact'                   , 'Contact'                   , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'phone'       ,  5, 'Phone Number'              , 'Phone Number'              , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fax'         ,  6, 'Fax Number'                , 'Fax Number'                , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_for_fax'  ,  7, 'Confirmation To This Fax'  , 'Confirmation To This Fax'  , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'email'       ,  8, 'Email'                     , 'Email'                     , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_for_email',  9, 'Confirmation To This Email', 'Confirmation To This Email', 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     , 10, 'Loguser'                   , 'Loguser'                   , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     , 11, 'Logtime'                   , 'Logtime'                   , 0, 0, 0, '', 0,   0, 0, '', 0, 11, 150, 'TextEdit', @loguser, @dt;
    

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_contact_log';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_contact_log Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_local.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Betsy
 日期 : 2017-11-22
 內容 : afos_client_local
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_local] (
	[lno]               	INT NOT NULL,
	[cust_no]           	VARCHAR(13) NOT NULL,
	[legal_name]        	VARCHAR(150) NOT NULL,
	[custodian]         	NVARCHAR(10) NOT NULL,
	[acc_name ]         	NVARCHAR(150) NOT NULL,
	[acc_open_date]     	DATE NOT NULL,
	[cp_type]           	SMALLINT NOT NULL,
	[caddress]          	NVARCHAR(200) NOT NULL,
	[tax_id_im]         	VARCHAR(8) NOT NULL,
	[cbc_acc_no]        	VARCHAR(4) NOT NULL,
	[approval_no]       	NVARCHAR(100) NOT NULL,
	[remark]            	NVARCHAR(150) NOT NULL,
	[instruction]       	NVARCHAR(350) NOT NULL,
	[cbrief_bank]       	VARCHAR(4) NOT NULL,
	[cosmos_cp]         	VARCHAR(60) NOT NULL,
	[cbrief_im]         	NVARCHAR(10) NOT NULL,
	[is_streetfx]       	BIT NOT NULL,
	[otc_cp_type]       	SMALLINT NOT NULL,
	[oct_cp_entity_type]	SMALLINT NOT NULL,
	[tax_id_fund]       	VARCHAR(8) NOT NULL,
	[cname_ben]         	NVARCHAR(100) NOT NULL,
	[is_mca_signed]     	BIT NOT NULL,
	[is_fini]           	BIT NOT NULL,
	[is_use_sh_frm_im]  	BIT NOT NULL,
	[is_quota_required] 	BIT NOT NULL,
	[is_net_settlement] 	BIT NOT NULL,
	[is_remit_fee_waved]	BIT NOT NULL,
	[cfm_submit_type]   	SMALLINT NOT NULL,
	[cfm_rec_type]      	SMALLINT NOT NULL,
	[cfm_chk_type]      	SMALLINT NOT NULL,
	[status]            	SMALLINT NOT NULL,
	[mod_status]        	SMALLINT NOT NULL,
	[Q-ID]              	CHAR(2) NOT NULL,
	[loguser]           	VARCHAR(20) NOT NULL,
	[logtime]           	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_local]') AND type in (N'U'))
	EXEC sp_backup_data 'afos_client_local', 'Tmp_afos_client_local'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_local]') AND type in (N'U'))
	DROP TABLE afos_client_local;	
	
EXEC sp_rename 'Tmp_afos_client_local', 'afos_client_local', 'OBJECT'
GO	

ALTER TABLE [dbo].[afos_client_local] ADD CONSTRAINT [PK_afos_client_local] PRIMARY KEY CLUSTERED
(
	[lno]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'afos_client_local', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_local', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'CIF Local';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'lno'               ,  1, ''                                     , ''                                     , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cust_no'           ,  2, 'Customer Number'                      , 'Customer Number'                      , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'legal_name'        ,  3, 'Legal Name'                           , 'Legal Name'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'custodian'         ,  4, 'Custodian Bank'                       , 'Custodian Bank'                       , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc_name '         ,  5, 'Account Name'                         , 'Account Name'                         , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc_open_date'     ,  6, 'Account Open Date'                    , 'Account Open Date'                    , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cp_type'           ,  7, 'Counterparty Type'                    , 'Counterparty Type'                    , 0, 0, 0, '', 0,  -1, 0, '', 1,  7, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'caddress'          ,  8, 'Client Chinese Address'               , 'Client Chinese Address'               , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tax_id_im'         ,  9, 'IM TAX ID'                            , 'IM TAX ID'                            , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbc_acc_no'        , 10, 'CBC Account No'                       , 'CBC Account No'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'approval_no'       , 11, 'Approval No.'                         , 'Approval No.'                         , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark'            , 12, 'Remark'                               , 'Remark'                               , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'instruction'       , 13, 'Standing Instruction'                 , 'Standing Instruction'                 , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbrief_bank'       , 14, 'Bank Short Name With Broker Taipei FX', 'Bank Short Name With Broker Taipei FX', 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cosmos_cp'         , 15, 'Counterparty For Cosmos'              , 'Counterparty For Cosmos'              , 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbrief_im'         , 16, 'IM Chinese Short Name'                , 'IM Chinese Short Name'                , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_streetfx'       , 17, 'StreetFx Indicator'                   , 'StreetFx Indicator'                   , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'otc_cp_type'       , 18, 'OTC Counterparty Type'                , 'OTC Counterparty Type'                , 0, 0, 0, '', 0,  -1, 0, '', 1, 18, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'oct_cp_entity_type', 19, 'OTC Counterparty '                    , 'OTC Counterparty '                    , 0, 0, 0, '', 0,  -1, 0, '', 1, 19, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tax_id_fund'       , 20, 'OCT TAX ID'                           , 'OCT TAX ID'                           , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname_ben'         , 21, 'Ben Name(IBRS)'                       , 'Ben Name(IBRS)'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_mca_signed'     , 22, 'MCA'                                  , 'MCA'                                  , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_fini'           , 23, 'Is FINI'                              , 'Is FINI'                              , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_use_sh_frm_im'  , 24, 'Short Form(IM Level)'                 , 'Short Form(IM Level)'                 , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_quota_required' , 25, 'Quota Required'                       , 'Quota Required'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_net_settlement' , 26, 'Is Net Settlement'                    , 'Is Net Settlement'                    , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_remit_fee_waved', 27, 'Is Remittance Fee Waved'              , 'Is Remittance Fee Waved'              , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_submit_type'   , 28, 'Trade Confirmation Submit Type'       , 'Trade Confirmation Submit Type'       , 0, 0, 0, '', 0,  -1, 0, '', 1, 28, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_rec_type'      , 29, 'Trade ConfirmationReceive Type'       , 'Trade ConfirmationReceive Type'       , 0, 0, 0, '', 0,  -1, 0, '', 1, 29, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_chk_type'      , 30, 'Trade Confirmation Check Type'        , 'Trade Confirmation Check Type'        , 0, 0, 0, '', 0,  -1, 0, '', 1, 30, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'status'            , 31, 'Status'                               , 'Status'                               , 0, 0, 0, '', 0,  -1, 0, '', 1, 31, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'mod_status'        , 32, 'Modifying Status'                     , 'Modifying Status'                     , 0, 0, 0, '', 0,  -1, 0, '', 1, 32, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'Q-ID'              , 33, 'Q Id'                                 , 'Q Id'                                 , 0, 0, 0, '', 0,   0, 0, '', 1, 33, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'           , 34, 'Loguser'                              , 'Loguser'                              , 0, 0, 0, '', 0,   0, 0, '', 0, 34, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'           , 35, 'Logtime'                              , 'Logtime'                              , 0, 0, 0, '', 0,   0, 0, '', 0, 35, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_local';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_local Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_local_edit.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Betsy
 日期 : 2017-11-22
 內容 : afos_client_local_edit
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_local_edit] (
	[seq]               	INT NOT NULL,
	[lno]               	INT NOT NULL,
	[cust_no]           	VARCHAR(13) NOT NULL,
	[legal_name]        	VARCHAR(150) NOT NULL,
	[custodian]         	NVARCHAR(10) NOT NULL,
	[acc_name ]         	NVARCHAR(150) NOT NULL,
	[acc_open_date]     	DATE NOT NULL,
	[cp_type]           	SMALLINT NOT NULL,
	[caddress]          	NVARCHAR(200) NOT NULL,
	[tax_id_im]         	VARCHAR(8) NOT NULL,
	[cbc_acc_no]        	VARCHAR(4) NOT NULL,
	[approval_no]       	NVARCHAR(100) NOT NULL,
	[remark]            	NVARCHAR(150) NOT NULL,
	[instruction]       	NVARCHAR(350) NOT NULL,
	[cbrief_bank]       	VARCHAR(4) NOT NULL,
	[cosmos_cp]         	VARCHAR(60) NOT NULL,
	[cbrief_im]         	NVARCHAR(10) NOT NULL,
	[is_streetfx]       	BIT NOT NULL,
	[otc_cp_type]       	SMALLINT NOT NULL,
	[oct_cp_entity_type]	SMALLINT NOT NULL,
	[tax_id_fund]       	VARCHAR(8) NOT NULL,
	[cname_ben]         	NVARCHAR(100) NOT NULL,
	[is_mca_signed]     	BIT NOT NULL,
	[is_fini]           	BIT NOT NULL,
	[is_use_sh_frm_im]  	BIT NOT NULL,
	[is_quota_required] 	BIT NOT NULL,
	[is_net_settlement] 	BIT NOT NULL,
	[is_remit_fee_waved]	BIT NOT NULL,
	[cfm_sub_type]      	SMALLINT NOT NULL,
	[cfm_rec_type]      	SMALLINT NOT NULL,
	[cfm_chk_type]      	SMALLINT NOT NULL,
	[status]            	SMALLINT NOT NULL,
	[mod_status]        	SMALLINT NOT NULL,
	[Q-ID]              	CHAR(2) NOT NULL,
	[loguser]           	VARCHAR(20) NOT NULL,
	[logtime]           	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_local_edit]') AND type in (N'U'))
	EXEC sp_backup_data 'afos_client_local_edit', 'Tmp_afos_client_local_edit'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_local_edit]') AND type in (N'U'))
	DROP TABLE afos_client_local_edit;	
	
EXEC sp_rename 'Tmp_afos_client_local_edit', 'afos_client_local_edit', 'OBJECT'
GO	

ALTER TABLE [dbo].[afos_client_local_edit] ADD CONSTRAINT [PK_afos_client_local_edit] PRIMARY KEY CLUSTERED
(
	[seq],[lno]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'afos_client_local_edit', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_local_edit', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'CIF Local Edit';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'seq'               ,  1, '異動序號'                             , '異動序號'                             , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lno'               ,  2, '客戶代碼'                             , '客戶代碼'                             , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cust_no'           ,  3, 'Customer Number'                      , 'Customer Number'                      , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'legal_name'        ,  4, 'Legal Name'                           , 'Legal Name'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'custodian'         ,  5, 'Custodian Bank'                       , 'Custodian Bank'                       , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc_name '         ,  6, 'Account Name'                         , 'Account Name'                         , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc_open_date'     ,  7, 'Account Open Date'                    , 'Account Open Date'                    , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cp_type'           ,  8, 'Counterparty Type'                    , 'Counterparty Type'                    , 0, 0, 0, '', 0,  -1, 0, '', 1,  8, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'caddress'          ,  9, 'Client Chinese Address'               , 'Client Chinese Address'               , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tax_id_im'         , 10, 'IM TAX ID'                            , 'IM TAX ID'                            , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbc_acc_no'        , 11, 'CBC Account No'                       , 'CBC Account No'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'approval_no'       , 12, 'Approval No.'                         , 'Approval No.'                         , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark'            , 13, 'Remark'                               , 'Remark'                               , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'instruction'       , 14, 'Standing Instruction'                 , 'Standing Instruction'                 , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbrief_bank'       , 15, 'Bank Short Name With Broker Taipei FX', 'Bank Short Name With Broker Taipei FX', 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cosmos_cp'         , 16, 'Counterparty For Cosmos'              , 'Counterparty For Cosmos'              , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbrief_im'         , 17, 'IM Chinese Short Name'                , 'IM Chinese Short Name'                , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_streetfx'       , 18, 'StreetFx Indicator'                   , 'StreetFx Indicator'                   , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'otc_cp_type'       , 19, 'OTC Counterparty Type'                , 'OTC Counterparty Type'                , 0, 0, 0, '', 0,  -1, 0, '', 1, 19, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'oct_cp_entity_type', 20, 'OTC Counterparty '                    , 'OTC Counterparty '                    , 0, 0, 0, '', 0,  -1, 0, '', 1, 20, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tax_id_fund'       , 21, 'OCT TAX ID'                           , 'OCT TAX ID'                           , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname_ben'         , 22, 'Ben Name(IBRS)'                       , 'Ben Name(IBRS)'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_mca_signed'     , 23, 'MCA'                                  , 'MCA'                                  , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_fini'           , 24, 'Is FINI'                              , 'Is FINI'                              , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_use_sh_frm_im'  , 25, 'Short Form(IM Level)'                 , 'Short Form(IM Level)'                 , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_quota_required' , 26, 'Quota Required'                       , 'Quota Required'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_net_settlement' , 27, 'Is Net Settlement'                    , 'Is Net Settlement'                    , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_remit_fee_waved', 28, 'Is Remittance Fee Waved'              , 'Is Remittance Fee Waved'              , 0, 0, 0, '', 0,   0, 0, '', 1, 28, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_sub_type'      , 29, 'Trade Confirmation Submit Type'       , 'Trade Confirmation Submit Type'       , 0, 0, 0, '', 0,  -1, 0, '', 1, 29, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_rec_type'      , 30, 'Trade ConfirmationReceive Type'       , 'Trade ConfirmationReceive Type'       , 0, 0, 0, '', 0,  -1, 0, '', 1, 30, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_chk_type'      , 31, 'Trade Confirmation Check Type'        , 'Trade Confirmation Check Type'        , 0, 0, 0, '', 0,  -1, 0, '', 1, 31, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'status'            , 32, 'Status'                               , 'Status'                               , 0, 0, 0, '', 0,  -1, 0, '', 1, 32, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'mod_status'        , 33, 'Modifying Status'                     , 'Modifying Status'                     , 0, 0, 0, '', 0,  -1, 0, '', 1, 33, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'Q-ID'              , 34, 'Q Id'                                 , 'Q Id'                                 , 0, 0, 0, '', 0,   0, 0, '', 1, 34, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'           , 35, 'Loguser'                              , 'Loguser'                              , 0, 0, 0, '', 0,   0, 0, '', 0, 35, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'           , 36, 'Logtime'                              , 'Logtime'                              , 0, 0, 0, '', 0,   0, 0, '', 0, 36, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_local_edit';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_local_edit Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_local_log.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-02
 內容 : afos_client_local_log
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_local_log] (
    [seq]                   INT NOT NULL,
    [lno]                   INT NOT NULL,
    [cust_no]               VARCHAR(13) NOT NULL,
    [legal_name]            VARCHAR(150) NOT NULL,
    [custodian]             NVARCHAR(10) NOT NULL,
    [acc_name]              NVARCHAR(150) NOT NULL,
    [acc_open_date]         DATE NOT NULL,
    [cp_type]               SMALLINT NOT NULL,
    [caddress]              NVARCHAR(200) NOT NULL,
    [tax_id_im]             VARCHAR(8) NOT NULL,
    [cbc_acc_no]            VARCHAR(4) NOT NULL,
    [approval_no]           NVARCHAR(100) NOT NULL,
    [remark]                NVARCHAR(150) NOT NULL,
    [instruction]           NVARCHAR(350) NOT NULL,
    [cbrief_bank]           VARCHAR(4) NOT NULL,
    [cosmos_cp]             VARCHAR(60) NOT NULL,
    [cbrief_im]             NVARCHAR(10) NOT NULL,
    [is_streetfx]           BIT NOT NULL,
    [otc_cp_type]           SMALLINT NOT NULL,
    [otc_cp_entity_type]    SMALLINT NOT NULL,
    [tax_id_fund]           VARCHAR(8) NOT NULL,
    [cname_ben]             NVARCHAR(100) NOT NULL,
    [is_mca_signed]         BIT NOT NULL,
    [is_fini]               BIT NOT NULL,
    [is_use_sh_frm_im]      BIT NOT NULL,
    [is_quota_required]     BIT NOT NULL,
    [is_net_settlement]     BIT NOT NULL,
    [is_remit_fee_waved]    BIT NOT NULL,
    [cfm_submit_type]       SMALLINT NOT NULL,
    [cfm_rec_type]          SMALLINT NOT NULL,
    [cfm_chk_type]          SMALLINT NOT NULL,
    [status]                SMALLINT NOT NULL,
    [mod_status]            SMALLINT NOT NULL,
    [loguser]               VARCHAR(20) NOT NULL,
    [logtime]               DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_local_log]') AND type in (N'U'))
    EXEC sp_backup_data 'afos_client_local_log', 'Tmp_afos_client_local_log'
    
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_local_log]') AND type in (N'U'))
    DROP TABLE afos_client_local_log;    
    
EXEC sp_rename 'Tmp_afos_client_local_log', 'afos_client_local_log', 'OBJECT'
GO    

ALTER TABLE [dbo].[afos_client_local_log] ADD CONSTRAINT [PK_afos_client_local_log] PRIMARY KEY CLUSTERED
(
    [seq],[lno]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'afos_client_local_log', 'ALL';
    
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_local_log', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'CIF Local Edit';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'seq'               ,  1, 'Sequecne'                             , 'Sequecne'                              , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'lno'               ,  2, 'Local No'                             , 'Local No'                              , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cust_no'           ,  3, 'Customer Number'                      , 'Customer Number'                       , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'legal_name'        ,  4, 'Legal Name'                           , 'Legal Name'                           , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'custodian'         ,  5, 'Custodian Bank'                       , 'Custodian Bank'                       , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc_name'          ,  6, 'Account Name'                         , 'Account Name'                         , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'acc_open_date'     ,  7, 'Account Open Date'                    , 'Account Open Date'                    , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cp_type'           ,  8, 'Counterparty Type'                    , 'Counterparty Type'                    , 0, 0, 0, '', 0,  -1, 0, '', 1,  8, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'caddress'          ,  9, 'Client Chinese Address'               , 'Client Chinese Address'               , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tax_id_im'         , 10, 'IM TAX ID'                            , 'IM TAX ID'                            , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbc_acc_no'        , 11, 'CBC Account No'                       , 'CBC Account No'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'approval_no'       , 12, 'Approval No.'                         , 'Approval No.'                         , 0, 0, 0, '', 0,   0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'remark'            , 13, 'Remark'                               , 'Remark'                               , 0, 0, 0, '', 0,   0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'instruction'       , 14, 'Standing Instruction'                 , 'Standing Instruction'                 , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbrief_bank'       , 15, 'Bank Short Name With Broker Taipei FX', 'Bank Short Name With Broker Taipei FX', 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cosmos_cp'         , 16, 'Counterparty For Cosmos'              , 'Counterparty For Cosmos'              , 0, 0, 0, '', 0,   0, 0, '', 1, 16, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cbrief_im'         , 17, 'IM Chinese Short Name'                , 'IM Chinese Short Name'                , 0, 0, 0, '', 0,   0, 0, '', 1, 17, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_streetfx'       , 18, 'StreetFx Indicator'                   , 'StreetFx Indicator'                   , 0, 0, 0, '', 0,   0, 0, '', 1, 18, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'otc_cp_type'       , 19, 'OTC Counterparty Type'                , 'OTC Counterparty Type'                , 0, 0, 0, '', 0,  -1, 0, '', 1, 19, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'otc_cp_entity_type', 20, 'OTC Counterparty '                    , 'OTC Counterparty '                    , 0, 0, 0, '', 0,  -1, 0, '', 1, 20, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'tax_id_fund'       , 21, 'OTC TAX ID'                           , 'OTC TAX ID'                           , 0, 0, 0, '', 0,   0, 0, '', 1, 21, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cname_ben'         , 22, 'Ben Name(IBRS)'                       , 'Ben Name(IBRS)'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 20, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_mca_signed'     , 23, 'MCA'                                  , 'MCA'                                  , 0, 0, 0, '', 0,   0, 0, '', 1, 22, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_fini'           , 24, 'Is FINI'                              , 'Is FINI'                              , 0, 0, 0, '', 0,   0, 0, '', 1, 23, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_use_sh_frm_im'  , 25, 'Short Form(IM Level)'                 , 'Short Form(IM Level)'                 , 0, 0, 0, '', 0,   0, 0, '', 1, 24, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_quota_required' , 26, 'Quota Required'                       , 'Quota Required'                       , 0, 0, 0, '', 0,   0, 0, '', 1, 25, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_net_settlement' , 27, 'Is Net Settlement'                    , 'Is Net Settlement'                    , 0, 0, 0, '', 0,   0, 0, '', 1, 26, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'is_remit_fee_waved', 28, 'Is Remittance Fee Waved'              , 'Is Remittance Fee Waved'              , 0, 0, 0, '', 0,   0, 0, '', 1, 27, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_submit_type'   , 29, 'Trade Confirmation Submit Type'       , 'Trade Confirmation Submit Type'       , 0, 0, 0, '', 0,  -1, 0, '', 1, 28, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_rec_type'      , 30, 'Trade ConfirmationReceive Type'       , 'Trade ConfirmationReceive Type'       , 0, 0, 0, '', 0,  -1, 0, '', 1, 29, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cfm_chk_type'      , 31, 'Trade Confirmation Check Type'        , 'Trade Confirmation Check Type'        , 0, 0, 0, '', 0,  -1, 0, '', 1, 30, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'status'            , 32, 'Status'                               , 'Status'                               , 0, 0, 0, '', 0,  -1, 0, '', 1, 31, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'mod_status'        , 33, 'Modifying Status'                     , 'Modifying Status'                     , 0, 0, 0, '', 0,  -1, 0, '', 1, 32, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'           , 34, 'Loguser'                              , 'Loguser'                              , 0, 0, 0, '', 0,   0, 0, '', 0, 33, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'           , 35, 'Logtime'                              , 'Logtime'                              , 0, 0, 0, '', 0,   0, 0, '', 0, 34, 150, 'DateEdit', @loguser, @dt;
    

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_local_log';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_local_log Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_remit_class.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-02
 內容 : afos_client_remit_class
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_remit_class] (
    [lno]           INT NOT NULL,
    [type]          SMALLINT NOT NULL,
    [trade_type]    SMALLINT NOT NULL,
    [code]          VARCHAR(3) NOT NULL,
    [loguser]       VARCHAR(20) NOT NULL,
    [logtime]       DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_remit_class]') AND type in (N'U'))
    EXEC sp_backup_data 'afos_client_remit_class', 'Tmp_afos_client_remit_class'
    
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_remit_class]') AND type in (N'U'))
    DROP TABLE afos_client_remit_class;    
    
EXEC sp_rename 'Tmp_afos_client_remit_class', 'afos_client_remit_class', 'OBJECT'
GO    

ALTER TABLE [dbo].[afos_client_remit_class] ADD CONSTRAINT [PK_afos_client_remit_class] PRIMARY KEY CLUSTERED
(
    [lno], [type], [trade_type], [code]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'afos_client_remit_class', 'ALL';
    
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_remit_class', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Contact';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'lno'         ,  1, 'lno'       , 'lno'          , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'type'        ,  2, 'Type'      , 'Type'         , 1, 1, 0, '', 0, 165, 0, '', 1,  2, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'trade_type'  ,  3, 'Trade Type', 'Trade Type'   , 1, 1, 0, '', 0, 513, 0, '', 1,  2, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'code'        ,  4, 'Code'      , 'Contact'      , 1, 1, 0, '', 0,   0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'     ,  6, 'Loguser'   , 'Loguser'      , 0, 0, 0, '', 0,   0, 0, '', 0,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'     ,  7, 'Logtime'   , 'Logtime'      , 0, 0, 0, '', 0,   0, 0, '', 0, 10, 150, 'TextEdit', @loguser, @dt;
    

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_remit_class';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_remit_class Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?b???z\afos_client_wss.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Alex
 日期 : 2017-09-02
 內容 : afos_client_wss
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_afos_client_wss] (
    [pno]                  INT NOT NULL,
    [wss_tid]              VARCHAR(15) NOT NULL,
    [cust_no]              VARCHAR(13) NOT NULL,
    [display_code]         VARCHAR(20) NOT NULL,
    [pno_im]               INT NOT NULL,
    [wss_tid_im]           VARCHAR(15) NOT NULL,
    [fund_code]            VARCHAR(20) NOT NULL,
    [fund_name]            VARCHAR(35) NOT NULL,
    [cp_type]              SMALLINT NOT NULL,
    [fund_type]            SMALLINT NOT NULL,
    [fund_location_type]   SMALLINT NOT NULL,
    [country]              VARCHAR(5) NOT NULL,
    [eaddress]             VARCHAR(175) NOT NULL,
    [swift_code]           VARCHAR(15) NOT NULL,
    [loguser]              VARCHAR(20) NOT NULL,
    [logtime]              DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_wss]') AND type in (N'U'))
    EXEC sp_backup_data 'afos_client_wss', 'Tmp_afos_client_wss'
    
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[afos_client_wss]') AND type in (N'U'))
    DROP TABLE afos_client_wss;    
    
EXEC sp_rename 'Tmp_afos_client_wss', 'afos_client_wss', 'OBJECT'
GO    

ALTER TABLE [dbo].[afos_client_wss] ADD CONSTRAINT [PK_afos_client_wss] PRIMARY KEY CLUSTERED
(
    [pno]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'afos_client_wss', 'ALL';
    
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'afos_client_wss', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'CIF WSS';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'pno'               ,  1, ''                             , ''                             , 1, 1, 0, '', 0,    0, 0, '', 1,  1, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'wss_tid'           ,  2, 'WSS No'                       , 'WSS No'                       , 0, 0, 0, '', 0,    0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt; 
INSERT #appTableField SELECT @tbname, 'cust_no'           ,  3, 'Customer Number'              , 'Customer Number'              , 0, 0, 0, '', 0,   0, 0, '', 1,  2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'display_code'      ,  4, 'WSS Display Code'             , 'WSS Display Code'             , 0, 0, 0, '', 0,    0, 0, '', 1,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'pno_im'            ,  5, ''                             , ''                             , 0, 0, 0, '', 0,    0, 0, '', 1,  4, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'wss_tid_im'        ,  6, 'IM WSS No'                    , 'IM WSS No'                    , 0, 0, 0, '', 0,    0, 0, '', 1,  5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fund_code'         ,  7, 'Fund Code'                    , 'Fund Code'                    , 0, 0, 0, '', 0,    0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fund_name'         ,  8, 'Fund Name'                    , 'Fund Name'                    , 0, 0, 0, '', 0,    0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'cp_type'           ,  9, 'Counterparty Type'            , 'Counterparty Type'            , 0, 0, 0, '', 0,  501, 0, '', 1,  8, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fund_type'         , 10, 'Fund Type'                    , 'Fund Type'                    , 0, 0, 0, '', 0,  502, 0, '', 1,  9, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'fund_location_type', 11, 'Fund Location Type'           , 'Fund Location Type'           , 0, 0, 0, '', 0,  503, 0, '', 1, 10, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'country'           , 12, 'Fund Domicile'                , 'Fund Domicile'                , 0, 0, 0, '', 0,    0, 0, '', 1, 11, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'eaddress'          , 13, 'Client Or Sub English Address', 'Client Or Sub English Address', 0, 0, 0, '', 0,    0, 0, '', 1, 12, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'swift_code'        , 14, 'SWIFT'                        , 'SWIFT'                        , 0, 0, 0, '', 0,    0, 0, '', 1, 13, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'           , 15, 'Loguser'                      , 'Loguser'                      , 0, 0, 0, '', 0,    0, 0, '', 0, 14, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'           , 16, 'Logtime'                      , 'Logtime'                      , 0, 0, 0, '', 0,    0, 0, '', 0, 15, 150, 'DateEdit', @loguser, @dt;
    

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'afos_client_wss';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table afos_client_wss Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?Ƶ{\app_scheduler_def.sql"  
/*---------------------------------
作者 : 吳欣融
版本 : 1.0.0
日期 : 2014/4/17
---------------------------------*/
BEGIN TRANSACTION
SET QUOTED_IDENTIFIER ON
SET ARITHABORT ON
SET NUMERIC_ROUNDABORT OFF
SET CONCAT_NULL_YIELDS_NULL ON
SET ANSI_NULLS ON
SET ANSI_PADDING ON
SET ANSI_WARNINGS ON
COMMIT

BEGIN TRANSACTION
--1.建立新Table
CREATE TABLE [dbo].[Tmp_app_scheduler_def] (
	[sid]                VARCHAR(20) NOT NULL,
	[name]               VARCHAR(40) NOT NULL,
	[stype]              SMALLINT NOT NULL,
	[daynum]             INT NOT NULL,
	[time]               DATETIME NOT NULL,
	[active]             BIT NOT NULL,
	[schedulercalendar]  VARCHAR(10) NOT NULL,
	[loguser]            VARCHAR(20) NOT NULL,
	[logtime]            DATETIME NOT NULL
);

--2.備份舊有資料(如果Table已經存在時)
IF EXISTS (SELECT * FROM sys.objects 
	WHERE object_id = OBJECT_ID(N'[dbo].[app_scheduler_def]') AND type in (N'U'))
	EXEC sp_backup_data 'app_scheduler_def', 'Tmp_app_scheduler_def'

--3.刪除舊有Table(如果已經存在時)
IF EXISTS (SELECT * FROM sys.objects
	WHERE object_id = OBJECT_ID(N'[dbo].[app_scheduler_def]') AND type in (N'U'))
	DROP TABLE app_scheduler_def;

--4.變更新Table名稱
EXEC sp_rename 'Tmp_app_scheduler_def', 'app_scheduler_def', 'OBJECT'
GO

ALTER TABLE [dbo].[app_scheduler_def] ADD 
	CONSTRAINT [PK_app_scheduler_def] PRIMARY KEY  CLUSTERED 
	(
	  [sid]
	)  ON [PRIMARY] 
GO

--6.完成(買單).....
COMMIT;
--7.還要再給權限才能讀寫喔~~
IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
EXEC sp_app_grant 'app_scheduler_def', 'ALL';
--第二階段：更新欄位說明================================================================================================
SET NOCOUNT ON; BEGIN TRAN; 
  DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT; 
  SELECT @tbname = 'app_scheduler_def', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1); 
  SELECT @owfield = 1, @owoption = 1; 
  DELETE app_table WHERE tablename = @tbname; 
  INSERT app_table SELECT @tbname, ''; 
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0; 
INSERT #appTableField SELECT @tbname, 'sid'              , 1, '排程代碼'    , '排程代碼'    , 1, 1, 0, '', 0, 0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'             , 2, '排程名稱'    , '排程名稱'    , 0, 0, 0, '', 0, 0, 0, '', 1, 2, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'stype'            , 3, '排程執行週期', '排程執行週期', 0, 0, 0, '', 0, 110, 0, '', 1, 3, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'daynum'           , 4, '天數'         , '天數'        , 0, 0, 0, '', 0, 0, 0, '', 1, 4, 150, 'SpinEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'time'             , 5, '時間(24H)'    , '時間(24H)'   , 0, 0, 0, '', 0, 0, 0, '', 1, 5, 150, 'TimeEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'active'           , 6, '有效'         , '有效'        , 0, 0, 0, '', 0, 0, 0, '', 1, 6, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'schedulercalendar', 7, '排程行事曆'  , '排程行事曆'      , 0, 0, 0, '', 0, 0, 0, '', 1, 6, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'          , 8, '異動人員'    , '異動人員'    , 0, 0, 0, '', 0, 0, 0, '', 1, 7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'          , 9, '異動時間'    , '異動時間'    , 0, 0, 0, '', 0, 0, 0, '', 1, 8, 150, 'TextEdit', @loguser, @dt;

IF @owfield=1 
  BEGIN 
    DELETE app_table_field WHERE tablename = @tbname; 
    INSERT app_table_field SELECT * FROM #appTableField; 
  END 
  ELSE 
    INSERT app_table_field SELECT * FROM #appTableField a 
     WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname); 
  DROP TABLE #appTableField; 
--將欄位次序調整成與 Table Scheme 相同 
  UPDATE a SET a.field_idx=c.colorder 
    FROM sysobjects m, syscolumns c, systypes t, app_table_field a 
   WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1 
     AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_scheduler_def';  
--更新欄位選項及說明 
  SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0; 
  SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0; 
IF @owoption=1 
  BEGIN 
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option SELECT * FROM #appTableFieldo; 
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo); 
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi; 
  END ELSE BEGIN 
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no); 
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a 
       WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no); 
  END;  
  DROP TABLE #appTableFieldo, #appTableFieldoi; 
 
IF @@ERROR>0 
  ROLLBACK 
ELSE 
  COMMIT 
GO 
 
PRINT '更新 app_scheduler_def 結束!' 
GO 
SET ANSI_PADDING OFF
GO


GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?Ƶ{\app_scheduler_log.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2014-08-29
 內容 : app_scheduler_log
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_scheduler_log] (
	[execdate]	DATETIME NOT NULL,
	[sid]     	VARCHAR(20) NOT NULL,
	[name]    	VARCHAR(40) NOT NULL,
	[enddate] 	DATETIME NOT NULL,
	[success] 	BIT NOT NULL,
	[logmsg]  	VARCHAR(1000) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_scheduler_log]') AND type in (N'U'))
	EXEC sp_backup_data 'app_scheduler_log', 'Tmp_app_scheduler_log'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_scheduler_log]') AND type in (N'U'))
	DROP TABLE app_scheduler_log;	
	
EXEC sp_rename 'Tmp_app_scheduler_log', 'app_scheduler_log', 'OBJECT'
GO	

ALTER TABLE [dbo].[app_scheduler_log] ADD CONSTRAINT [PK_app_scheduler_log] PRIMARY KEY CLUSTERED
(
	[execdate],[sid]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_scheduler_log', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_scheduler_log', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'app_scheduler_log';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'execdate',  1, 'execdate', 'execdate', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'sid'     ,  2, 'sid'     , 'sid'     , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'    ,  3, 'name'    , 'name'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'enddate' ,  4, 'enddate' , 'enddate' , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'success' ,  5, 'success' , 'success' , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logmsg'  ,  6, 'logmsg'  , 'logmsg'  , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_scheduler_log';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_scheduler_log Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?Ƶ{\app_scheduler_loglist.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : frank
 日期 : 2014-06-09
 內容 : app_scheduler_loglist
---------------------------------*/
BEGIN TRANSACTION 

CREATE TABLE [dbo].[Tmp_app_scheduler_loglist] (
	[execdate]	DATETIME NOT NULL,
	[sid]     	VARCHAR(20) NOT NULL,
	[jobindex]	INT NOT NULL,
	[jobname] 	VARCHAR(100) NOT NULL,
	[id]      	VARCHAR(20) NOT NULL,
	[name]    	VARCHAR(80) NOT NULL,
	[iotype]  	SMALLINT NOT NULL,
	[rundate] 	DATETIME NOT NULL,
	[source]  	VARCHAR(100) NOT NULL,
	[target]  	VARCHAR(100) NOT NULL,
	[success] 	BIT NOT NULL,
	[sname]   	VARCHAR(40) NOT NULL,
	[logmsg]  	VARCHAR(4000) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_scheduler_loglist]') AND type in (N'U'))
	EXEC sp_backup_data 'app_scheduler_loglist', 'Tmp_app_scheduler_loglist'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_scheduler_loglist]') AND type in (N'U'))
	DROP TABLE app_scheduler_loglist;

EXEC sp_rename 'Tmp_app_scheduler_loglist', 'app_scheduler_loglist', 'OBJECT'
GO

ALTER TABLE [dbo].[app_scheduler_loglist] ADD CONSTRAINT [PK_app_scheduler_loglist] PRIMARY KEY CLUSTERED
(
	[execdate],[sid],[jobindex],[id],[rundate]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_scheduler_loglist', 'ALL';

--Update Columns Description
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_scheduler_loglist', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'app_scheduler_loglist';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'execdate',  1, '排程時間'    , '排程時間'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'sid'     ,  2, '排程代碼'    , '排程代碼'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'jobindex',  3, '工作序號'    , '工作序號'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'jobname' ,  4, '工作名稱'    , '工作名稱'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'id'      ,  5, '匯入設定代碼', '匯入設定代碼', 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'name'    ,  6, '匯入設定名稱', '匯入設定名稱', 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'iotype'  ,  7, '作業型態'    , '作業型態'    , 0, 0, 0, '', 0, 104, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'rundate' ,  8, '作業時間'    , '作業時間'    , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'source'  ,  9, '資料來源'    , '資料來源'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'target'  , 10, '目標資料庫'  , '目標資料庫'  , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'success' , 11, '成功'        , '成功'        , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'sname'   , 12, '排程名稱'    , '排程名稱'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logmsg'  , 13, 'LOG'         , 'LOG'         , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

--Reorder Columns to be same as Table Schema
UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_scheduler_loglist';

--Update Option for Columns
SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_scheduler_loglist Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\?Ƶ{\app_scheduler_set.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2014-08-29
 內容 : app_scheduler_set
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_app_scheduler_set] (
	[sid]       	VARCHAR(20) NOT NULL,
	[jobindex]  	INT NOT NULL,
	[snote]     	VARCHAR(40) NOT NULL,
	[execdatetp]	SMALLINT NOT NULL,
	[active]    	BIT NOT NULL,
	[loguser]   	VARCHAR(20) NOT NULL,
	[logtime]   	DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_scheduler_set]') AND type in (N'U'))
	EXEC sp_backup_data 'app_scheduler_set', 'Tmp_app_scheduler_set'
	
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[app_scheduler_set]') AND type in (N'U'))
	DROP TABLE app_scheduler_set;	
	
EXEC sp_rename 'Tmp_app_scheduler_set', 'app_scheduler_set', 'OBJECT'
GO	

ALTER TABLE [dbo].[app_scheduler_set] ADD CONSTRAINT [PK_app_scheduler_set] PRIMARY KEY CLUSTERED
(
	[sid],[jobindex]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'app_scheduler_set', 'ALL';
	
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'app_scheduler_set', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'app_scheduler_set';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'sid'       ,  1, '排程代碼'       , '排程代碼'       , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'jobindex'  ,  2, '工作序號'  , '工作序號'  , 1, 1, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'snote'     ,  3, '說明'     , '說明'     , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'execdatetp',  4, '執行日期參數', '執行日期參數', 0, 0, 0, '', 0, 111, 0, '', 1, 1, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'active'    ,  5, '有效'    , '有效'    , 0, 0, 0, '', 0,   0, 0, '', 1, 1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'   ,  6, '異動人員'   , '異動人員'   , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'   ,  7, '異動時間'   , '異動時間'   , 0, 0, 0, '', 0,   0, 0, '', 0, 5, 150, 'DateEdit', @loguser, @dt;
	

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'app_scheduler_set';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table app_scheduler_set Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Table\??????\user_account_history_record.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : 000251
 日期 : 2017-07-18
 內容 : user_account_history_record
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_user_account_history_record] (
    [user]         VARCHAR(20) NOT NULL,
    [user_status]  SMALLINT NOT NULL,
    [create_time]  DATETIME NOT NULL,
    [exec_type]    SMALLINT NOT NULL,
    [loguser]      VARCHAR(20) NOT NULL,
    [logtime]      DATETIME NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[user_account_history_record]') AND type in (N'U'))
    EXEC sp_backup_data 'user_account_history_record', 'Tmp_user_account_history_record'
    
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[user_account_history_record]') AND type in (N'U'))
    DROP TABLE user_account_history_record;    
    
EXEC sp_rename 'Tmp_user_account_history_record', 'user_account_history_record', 'OBJECT'
GO    

ALTER TABLE [dbo].[user_account_history_record] ADD CONSTRAINT [PK_user_account_history_record] PRIMARY KEY CLUSTERED
(
    [user], [user_status], [create_time]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
    EXEC sp_app_grant 'user_account_history_record', 'ALL';
    
SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'user_account_history_record', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, 'Use Account History Record';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'user'       , 1, 'User'      , 'User'     , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'user_status', 2, 'Type'      , 'Type'     , 0, 0, 0, '', 0, 904, 0, '', 1,  2, 150, 'LookupEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'ceate_time' , 5, 'Ceate Time', 'Ceate Time'  , 0, 0, 0, '', 0,   0, 0, '', 0,  4, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'exec_type'  , 3, 'Exec Type' , 'Exec Type', 0, 0, 0, '', 0, 905, 0, '', 1,  2, 150, 'LookupEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'loguser'    , 4, 'Loguser'   , 'Loguser'  , 0, 0, 0, '', 0,   0, 0, '', 0,  3, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'logtime'    , 5, 'Logtime'   , 'Logtime'  , 0, 0, 0, '', 0,   0, 0, '', 0,  4, 150, 'DateEdit', @loguser, @dt;
    

IF @owfield=1
BEGIN
    DELETE app_table_field WHERE tablename = @tbname;
    INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
    INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'user_account_history_record';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;


IF @owoption=1
BEGIN
    DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option SELECT * FROM #appTableFieldo;
    DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
    INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
    INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
    INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
    WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table user_account_history_record Completely'
GO
SET ANSI_PADDING OFF
GO

GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Type\tp_cash_flow.sql"  
--日結資金異動暫存檔宣告
IF TYPE_ID(N'tp_cash_flow') IS NOT NULL
  DROP TYPE tp_cash_flow;

CREATE TYPE tp_cash_flow AS TABLE(
    pno               INT
  , [date]            DATE
  , seq               INT
  , trade_no          VARCHAR (40)
  , value_date        DATE
  , cp_type           SMALLINT       DEFAULT 0 
  ,	product_type      SMALLINT                          --商品類別
  ,	swap_sf           SMALLINT
  ,	type              SMALLINT
  ,	trade_status      SMALLINT       DEFAULT 0
  ,	orig_trade_no     VARCHAR(13)
  ,	orig_trade_amt	NUMERIC(20,5)    DEFAULT 0
  , trade_type		  SMALLINT
  , cb_trade_type	  CHAR(2)
  , ccy               CHAR (3)
  , amt_in            NUMERIC (20,5)
  , amt_out           NUMERIC (20,5)
  , exch_rate         NUMERIC (11,8)  DEFAULT 0
  , bal_amt           NUMERIC (20,5)                    --計算單筆 net (amt_in - amt_out)
  , note              VARCHAR (100)   DEFAULT ''
  , data_no           VARCHAR (12)    DEFAULT ''
  , code              CHAR (10)       DEFAULT ''
  , country_source    VARCHAR (5)     DEFAULT 'TW'      --預設帶入 'TW'
  , [class]           VARCHAR (3)     DEFAULT ''
  , class_detail      VARCHAR (3)     DEFAULT ''
  , kind_code         VARCHAR (3)     DEFAULT ''
  , forward_spl       VARCHAR (3)     DEFAULT ''
  , data_source       VARCHAR (3)     DEFAULT ''         --預設為空
  , data_kind         VARCHAR (3)     DEFAULT ''
  , oppo_name         VARCHAR (40)    DEFAULT ''
  , rem_type          VARCHAR (3)     DEFAULT '3'        --預設帶入 3.民間
  , swift_bank        VARCHAR (16)    DEFAULT ''
  , bank              VARCHAR (12)    DEFAULT ''
  , bankacc           VARCHAR (14)    DEFAULT ''
  , cp_bank           VARCHAR (12)    DEFAULT ''
  , cp_bankacc        VARCHAR (14)    DEFAULT ''
  , remit_type		  SMALLINT		  DEFAULT 0			 --僅提供出入金明細使用
  , approv_no_flag    VARCHAR(1) 
  , forward_settle    VARCHAR(3) 
);
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Type\tp_cb_cash_flow.sql"  
--央行申報資金暫存檔宣告
IF TYPE_ID(N'tp_cb_cash_flow') IS NOT NULL
  DROP TYPE tp_cb_cash_flow;

CREATE TYPE tp_cb_cash_flow AS TABLE(
    pno               INT                              --客戶代碼
  , [date]            DATE                             --日期
  , seq               INT                              --序號
  , trade_no          VARCHAR(40)                      --交易單號
  , value_date		  DATE                             --商品類別
  , cp_type           SMALLINT NOT NULL 
  ,	product_type      SMALLINT NOT NULL
  ,	swap_sf           SMALLINT
  ,	type              SMALLINT
  ,	trade_status      SMALLINT NOT NULL
  ,	orig_trade_no     VARCHAR(13)
  ,	orig_trade_amt	NUMERIC(20,5)    DEFAULT 0
  , trade_type		  SMALLINT		  				   --交易類別
  , cb_trade_type	  CHAR(2)						   --交易類型
  , ccy               CHAR(3)                          --幣別
  , amt_in            NUMERIC(20,5)                    --收入
  , amt_out           NUMERIC(20,5)                    --支出
  , exch_rate         NUMERIC(15,10) DEFAULT 0         --匯率
  , bal_amt           NUMERIC(20,5)                    --餘額計算單筆 net   --amt_in - amt_out
  , note              VARCHAR(100)   DEFAULT ''        --摘要
  , data_no           VARCHAR(12)    DEFAULT ''        --單據號碼
  , country_source    VARCHAR(5)     DEFAULT 'TW'      --地區國別           --預設帶入 'TW'
  , [class]           VARCHAR(3)     DEFAULT ''        --收支分類
  , class_detail      VARCHAR(3)     DEFAULT ''        --收支細分類
  , kind_code         VARCHAR(3)     DEFAULT ''        --交易日報類別
  , forward_spl       VARCHAR(3)     DEFAULT ''        --交易性質註記
  , data_source       VARCHAR(3)     DEFAULT ''        --外匯來源及去處     --預設為空
  , data_kind         VARCHAR(3)     DEFAULT ''        --解款及繳款方式
  , oppo_name         VARCHAR(40)    DEFAULT ''        --匯款/受款人戶名
  , rem_type          VARCHAR(3)     DEFAULT '3'       --匯/受款人身分別    --預設帶入 3.民間
  , swift_bank        VARCHAR(16)    DEFAULT ''        --匯款/受款人代號
  , data_source2      VARCHAR(1)     DEFAULT ''        --媒體檔案格式
  , bank              VARCHAR(12)    DEFAULT ''        --保管專戶銀行代號
  , bankacc           VARCHAR(14)    DEFAULT ''        --保管專戶銀行帳號
  , cp_bank           VARCHAR(12)    DEFAULT ''        --交易對手銀行代號
  , cp_bankacc        VARCHAR(14)    DEFAULT ''        --交易對手銀行帳號
  , approv_no_flag    VARCHAR(1) 
  , forward_settle    VARCHAR(3) 
);
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Type\tp_Privilege.sql"  
IF TYPE_ID(N'tp_Privilege') IS NOT NULL
  DROP TYPE tp_Privilege;

CREATE TYPE tp_Privilege AS TABLE(
  itempos	VARCHAR (15)
, runp	  BIT
, selectp	BIT
, insertp	BIT
, updatep	BIT
, deletep	BIT
, printp	BIT
, lockp	  BIT
, unlockp	BIT
, export	BIT
, setup	  BIT
);
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\Type\tp_UserAndRoleRelation.sql"  
IF TYPE_ID(N'tp_UserAndRoleRelation') IS NOT NULL
  DROP TYPE tp_UserAndRoleRelation;

CREATE TYPE tp_UserAndRoleRelation AS TABLE(
    parentkey INT
,   childkey  INT
,   parentid  VARCHAR (20)
,   childid   VARCHAR (20)
);
GO  
 
--"C:\Users\000356\source\repos\AFOS\dbscript\View\vw_contract.sql"  
if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[vw_contract]') and OBJECTPROPERTY(id, N'IsView') = 1)
    drop view [dbo].[vw_contract]
GO
/*---------------------------------
 版本 : 1.0.2
 日期 : 2017-11-21
 內容 : 增列pno_im, cfm_submit_type, cfm_rec_type, cfm_chk_type

 版本 : 1.0.1
 日期 : 2017-11-20
 內容 : 新增Customer Number

 版本 : 1.0.0
 日期 : 2017-11-01
 內容 : 系統契約總表
---------------------------------*/
CREATE VIEW [vw_contract]
AS 
    SELECT w.pno, 
		   w.cp_type AS cp_type_wss, 
		   ISNULL(l.cp_type, 0) AS cp_type_local, 
		   w.fund_name, 
		   ISNULL(w_im.fund_name, w.fund_name) AS fund_name_im, 
		   w.wss_tid AS cust_tid, 
		   w.cust_no AS cust_no, 
		   ISNULL(l.lno, 0) AS lno,
		   w.pno_im,
		   ISNULL(l.cfm_submit_type, 0) AS cfm_submit_type,
		   ISNULL(l.cfm_rec_type, 0) AS cfm_rec_type,
		   ISNULL(l.cfm_chk_type, 0) AS cfm_chk_type
      FROM afos_client_wss AS w
      LEFT JOIN afos_client_local AS l ON l.cust_no = w.cust_no
      LEFT JOIN afos_client_wss AS w_im ON w.pno_im = w_im.pno AND w.pno_im != 0
GO

IF EXISTS (SELECT 1 FROM sysobjects WHERE id=OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(id,'IsProcedure')=1)
   EXEC sp_app_grant 'vw_contract', 'SELECT'
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\SOURCE\tools\SpecCreator\Resources\template_sql.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : {0}
 日期 : {1}
 內容 : {2}
---------------------------------*/

BEGIN TRANSACTION
{3}
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[{2}]') AND type in (N'U'))
	EXEC sp_backup_data '{2}', 'Tmp_{2}'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[{2}]') AND type in (N'U'))
	DROP TABLE {2};

EXEC sp_rename 'Tmp_{2}', '{2}', 'OBJECT'
GO

{4}
COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant '{2}', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = '{2}', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '{5}';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
{6}
IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = '{2}';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

{7}
IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table {2} Completely'
GO
SET ANSI_PADDING OFF
GO
GO  
 
--"C:\Users\000356\source\repos\AFOS\SOURCE\tools\SpecCreator\UnitTest\Resources\test_table.sql"  
--This Script Is Created By SpecCreator
/*---------------------------------
 作者 : Tester
 日期 : 2017-02-09
 內容 : test_table
---------------------------------*/

BEGIN TRANSACTION
CREATE TABLE [dbo].[Tmp_test_table] (
	[key1]    	VARCHAR(20) NOT NULL,
	[key2]    	INT NOT NULL,
	[date1]   	DATE NOT NULL,
	[date2]   	DATETIME NOT NULL,
	[date3]   	SMALLDATETIME NOT NULL,
	[char1]   	CHAR(10) NOT NULL,
	[char2]   	NCHAR(10) NOT NULL,
	[char3]   	VARCHAR(10) NOT NULL,
	[char4]   	NVARCHAR(10) NOT NULL,
	[char5]   	NVARCHAR(MAX) NOT NULL,
	[bit1]    	BIT NOT NULL,
	[opt1]    	SMALLINT NOT NULL,
	[opt2]    	SMALLINT NOT NULL,
	[int1]    	INT NOT NULL,
	[numeric1]	NUMERIC(20,5) NOT NULL
);

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[test_table]') AND type in (N'U'))
	EXEC sp_backup_data 'test_table', 'Tmp_test_table'

IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[test_table]') AND type in (N'U'))
	DROP TABLE test_table;

EXEC sp_rename 'Tmp_test_table', 'test_table', 'OBJECT'
GO

ALTER TABLE [dbo].[test_table] ADD CONSTRAINT [PK_test_table] PRIMARY KEY CLUSTERED
(
    [key1],[key2]
)
ON [PRIMARY]
GO

COMMIT;

IF EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID('sp_app_grant') AND OBJECTPROPERTY(object_id,'IsProcedure')=1)
	EXEC sp_app_grant 'test_table', 'ALL';

SET NOCOUNT ON; BEGIN TRAN; DECLARE @tbname VARCHAR(40), @loguser VARCHAR(20), @dt DATETIME, @owfield BIT, @owoption BIT;
SELECT @tbname = 'test_table', @loguser = USER, @dt = ROUND(CONVERT(FLOAT, GETDATE()), 0, 1);
SELECT @owfield = 1, @owoption = 1;
DELETE app_table WHERE tablename = @tbname;
INSERT app_table SELECT @tbname, '測試資料表';
SELECT * INTO #appTableField FROM app_table_field WHERE 1 = 0;
INSERT #appTableField SELECT @tbname, 'key1'    ,  1, '測試主鍵1'  , '測試主鍵1'  , 1, 1, 0, '', 0,   0, 0, '', 1,  1, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'key2'    ,  2, '測試主鍵2'  , '測試主鍵2'  , 1, 1, 0, '', 0,   0, 0, '', 1,  2, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date1'   ,  3, '測試日期1'  , '測試日期1'  , 0, 0, 0, '', 0,   0, 0, '', 1,  3, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date2'   ,  4, '測試日期2'  , '測試日期2'  , 0, 0, 0, '', 0,   0, 0, '', 1,  4, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'date3'   ,  5, '測試日期3'  , '測試日期3'  , 0, 0, 0, '', 0,   0, 0, '', 1,  5, 150, 'DateEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'char1'   ,  6, '測試字串1'  , '測試字串1'  , 0, 0, 0, '', 0,   0, 0, '', 1,  6, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'char2'   ,  7, '測試字串2'  , '測試字串2'  , 0, 0, 0, '', 0,   0, 0, '', 1,  7, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'char3'   ,  8, '測試字串3'  , '測試字串3'  , 0, 0, 0, '', 0,   0, 0, '', 1,  8, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'char4'   ,  9, '測試字串4'  , '測試字串4'  , 0, 0, 0, '', 0,   0, 0, '', 1,  9, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'char5'   , 10, '測試字串5'  , '測試字串5'  , 0, 0, 0, '', 0,   0, 0, '', 1, 10, 150, 'TextEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'bit1'    , 11, '測試二元1'  , '測試二元1'  , 0, 0, 0, '', 0,   0, 0, '', 1, 11, 150, 'CheckEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'opt1'    , 12, '測試選項1'  , '測試選項1'  , 0, 0, 0, '', 0,   2, 0, '', 1, 12, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'opt2'    , 13, '測試選項2'  , '測試選項2'  , 0, 0, 0, '', 0,   8, 0, '', 1, 13, 150, 'LookUpEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'int1'    , 14, '測試整數1'  , '測試整數1'  , 0, 0, 0, '', 0,   0, 0, '', 1, 14, 150, 'CalcEdit', @loguser, @dt;
INSERT #appTableField SELECT @tbname, 'numeric1', 15, '測試浮點數1', '測試浮點數1', 0, 0, 0, '', 0,   0, 0, '', 1, 15, 150, 'CalcEdit', @loguser, @dt;

IF @owfield=1
BEGIN
	DELETE app_table_field WHERE tablename = @tbname;
	INSERT app_table_field SELECT * FROM #appTableField;
END
ELSE
	INSERT app_table_field SELECT * FROM #appTableField a WHERE NOT EXISTS (SELECT 1 FROM app_table_field WHERE tablename = a.tablename AND fieldname = a.fieldname);
DROP TABLE #appTableField;

UPDATE a SET a.field_idx=c.colorder
FROM sysobjects m, syscolumns c, systypes t, app_table_field a
WHERE m.id = c.id AND c.xtype = t.xtype AND OBJECTPROPERTY(m.id, 'IsUserTable') = 1
AND m.name = a.tablename AND c.name = a.fieldname AND m.name = 'test_table';

SELECT * INTO #appTableFieldo FROM app_table_field_option WHERE 1 = 0;
SELECT * INTO #appTableFieldoi FROM app_table_field_option_item WHERE 1 = 0;

INSERT #appTableFieldo SELECT 2, '2.測試選項1', 1;
INSERT #appTableFieldoi SELECT 2, 1, '1.買進', @loguser, @dt;
INSERT #appTableFieldoi SELECT 2, 2, '2.賣出', @loguser, @dt;

INSERT #appTableFieldo SELECT 8, '8.測試選項2', 1;
INSERT #appTableFieldoi SELECT 8, 1, '1.市價', @loguser, @dt;
INSERT #appTableFieldoi SELECT 8, 2, '2.限價', @loguser, @dt;

IF @owoption=1
BEGIN
	DELETE app_table_field_option WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option SELECT * FROM #appTableFieldo;
	DELETE app_table_field_option_item WHERE opt_no IN (SELECT opt_no FROM #appTableFieldo);
	INSERT app_table_field_option_item SELECT * FROM #appTableFieldoi;
END
ELSE
BEGIN
	INSERT app_table_field_option SELECT a.* FROM #appTableFieldo a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option WHERE opt_no = a.opt_no);
	INSERT app_table_field_option_item SELECT a.* FROM #appTableFieldoi a
	WHERE NOT EXISTS (SELECT 1 FROM app_table_field_option_item WHERE opt_no = a.opt_no AND item_no = a.item_no);
END;
DROP TABLE #appTableFieldo, #appTableFieldoi;

IF @@ERROR>0 ROLLBACK
ELSE COMMIT
GO

PRINT 'Update Table test_table Completely'
GO
SET ANSI_PADDING OFF
GO
GO  
 
