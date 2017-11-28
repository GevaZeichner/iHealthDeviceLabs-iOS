# iHealth SDK Release Note

### 1. V1.0.14
```
Description: SDK
Release Date: 2015-12-18
```

### 2. V1.0.15
```
Description: fix po3 bug
Release Date: 2016-3-7
```

### 3. V1.0.16
```
Description: More function for AM
Release Date: 2016-5-3
   a. Add dataID for measure result(BP BG HS AM PO),
   	  etc: {"weight":60,"dataID":"xxxxxxx"}  
   b. Add 'activityLevel' property for AM user, 'bmr' property is invalidate now.   
      activityLevel=1, Sedentary,spend most of day sitting.      
      activityLevel=2, Active,spend a good part of day doing some physical activity.  
      activityLevel=3, Very Active,spend most of day doing heavy physical activity.  
   c. Modify calories for AM, etc {Calories = 49,Step = 1213,TotalCalories = 656}  
      Calories is for sport only.  
      TotalCalories sum Calories and bmr.  
```
### 4. V1.0.17
```
Description: fix po3 measure again bug
Release Date: 2016-5-4
```


### 5. V2.0
```
Description: Add Scan and Connect function for iHealth device with low energy.
Release Date: 2016-5-5
```

```
Old version：SDK will scan and connect all iHealth Device automatically.
New version: SDK supply the Api for scan, and Api for connect Separately.

More info, please read class :
ScanDeviceController.h
ConnectDeviceController.h

More details, please read iHealth Demo App

```

### 6. V2.0.1
```
Description: Add Flow Chart, BG errorID.
Release Date: 2016-5-12
```

### 7. V2.1
```
Description:

1. Modify the authentication way, If you want to use the iHealth Device, you must first call authentication method, can call after certification by iHealth relevant methods of the device.
2. Method call any product authentication cancelled.
3. Add support Device:iHealth BP5S 、Continua BP
4. Support GDH code
5. upgrade SDKUpdateDevice Method  support file download progess
6. To optimize the demo program
7. To reconstruct the BP method is called
8. To optimize the interface calls, support the instruction cache

Release Date: 2017-5-5
```

### 8. V2.1.1
```
Description:

1. Support HS2  
2. Support the new device update method
3. Change  po3 method

old:
	--(void)commandPO3OfflineDataCount:(DisposePO3OfflineDataCount)offlineDataCount withStartUpload:(DisposePO3StartUpload)startUpload withOfflineData:(DisposePO3OfflineData)measureData withOfflineWaveData:(DisposePO3OfflineWaveData)offlineWaveData withFinishMeasure:(DisposePO3FinishUpload)finishUpload withErrorBlock:(DisposePO3ErrorBlock)errorBlock; 
new:
-(void)commandPO3OfflineDataCount:(DisposePO3OfflineDataCount)offlineDataCount withOfflineData:(DisposePO3OfflineData)offlineData withOfflineWaveData:(DisposePO3OfflineWaveData)offlineWaveData withFinishMeasure:(DisposePO3FinishUpload)finishUpload withErrorBlock:(DisposePO3ErrorBlock)errorBlock;

4. Change BP  stop measure  method name
5. BP5/7  result  add HSD
6. Change BG5

1）delete method  -(void)commandInitBGSetUnit:(BGUnit )unitState DisposeBGBottleID:(DisposeBGBottleID)disposeBGBottleID DisposeBGErrorBlock:(DisposeBGErrorBlock)disposeBGErrorBlock;

2）
old：
--(void)commandCreateBGtestStripInBlock:(DisposeBGStripInBlock)disposeBGStripInBlock DisposeBGBloodBlock:(DisposeBGBloodBlock)disposeBGBloodBlock DisposeBGResultBlock:(DisposeBGResultBlock)disposeBGResultBlock  DisposeBGTestModelBlock:(DisposeBGTestModelBlock)disposeBGTestModelBlock DisposeBGErrorBlock:(DisposeBGErrorBlock)disposeBGErrorBlock;
new：
-(void)commandCreateBGtestStripInBlock:(DisposeBGStripInBlock)disposeBGStripInBlock
                   DisposeBGBloodBlock:(DisposeBGBloodBlock)disposeBGBloodBlock
                  DisposeBGResultBlock:(DisposeBGResultBlock)disposeBGResultBlock
                   DisposeBGErrorBlock:(DisposeBGErrorBlock)disposeBGErrorBlock;
3）
old：
-(void)commandCreateBGtestModel:(BGMeasureMode)testMode DisposeBGStripInBlock:(DisposeBGStripInBlock)disposeBGStripInBlock DisposeBGBloodBlock:(DisposeBGBloodBlock)disposeBGBloodBlock DisposeBGResultBlock:(DisposeBGResultBlock)disposeBGResultBlock DisposeBGTestModelBlock:(DisposeBGTestModelBlock)disposeBGTestModelBlock  DisposeBGErrorBlock:(DisposeBGErrorBlock)disposeBGErrorBlock;
new：
-(void)commandCreateBGtestModel:(BGMeasureMode)testMode
         DisposeBGStripInBlock:(DisposeBGStripInBlock)disposeBGStripInBlock
           DisposeBGBloodBlock:(DisposeBGBloodBlock)disposeBGBloodBlock
           DisposeBGResultBlock:(DisposeBGResultBlock)disposeBGResultBlock
            DisposeBGErrorBlock:(DisposeBGErrorBlock)disposeBGErrorBlock;


Release Date: 2017-9-4
```

### 9. V2.1.2
```
Description:

1. Fix BP bug
2. Fix HS5 bug

Release Date: 2017-9-26
```

### 10. V2.1.3
```
Description:

1. Support BG5S  

2. support  THV3  TS28B

3. To optimize the user authentication method, the authentication method must be called first when using the SDK. You can use the SDK offline when the authentication is successful

4. Optimize the BG1 code，Change  BG1 method，The incoming parameters and return values are unchanged.

old:
	-(void)commandConnectBGwithDeviceModel:(NSNumber *)bg1Model DisposeDiscoverBlock:(DisposeDiscoverBGBlock)disposeDiscoverBGBlock DisposeBGIDPSBlock:(DisposeBGIDPSBlock)disposeBGIDPSBlock DisposeConnectBGBlock:(DisposeConnectBGBlock)disposeConnectBGBlock DisposeBGErrorBlock:(DisposeBGErrorBlock)disposeBGErrorBlock;

new:

     - (void)commandBG1DeviceModel:(NSNumber *)BG1Model withDiscoverBlock:(DisposeBG1DiscoverBlock)discover withDiscoverBlock:(DisposeBG1IDPSBlock)IDPSInfo withConnectBlock:(DisposeBG1ConnectBlock)connect withErrorBlock:(DisposeBG1ErrorBlock)error;


old：

-(void)commandCreateBGtestWithMeasureType:(BGMeasureMode)testType CodeType:(BGCodeMode)codeType CodeString:(NSString*)codeStrips DisposeBGSendCodeBlock:(DisposeBGSendCodeBlock)disposeBGSendCodeBlock DisposeBGStripInBlock:(DisposeBGStripInBlock)disposeBGStripInBlock DisposeBGBloodBlock:(DisposeBGBloodBlock)disposeBGBloodBlock DisposeBGResultBlock:(DisposeBGResultBlock)disposeBGResultBlock DisposeBGStripOutBlock:(DisposeBGStripOutBlock)disposeBGStripOutBlock DisposeBGErrorBlock:(DisposeBGErrorBlock)disposeBGErrorBlock;

new：
- (void)commandBG1MeasureMode:(BGMeasureMode)measureMode withCodeMode:(BGCodeMode)codeMode withCodeString:(NSString *)codeString withSendCodeResultBlock:(DisposeBG1SendCodeResultBlock)sendCodeResult withStripInBlock:(DisposeBGStripInBlock)stripIn withBloodBlock:(DisposeBGBloodBlock)blood withResultBlock:(DisposeBGResultBlock)measureResult withStripOutBlock:(DisposeBGStripOutBlock)stripOut withErrorBlock:(DisposeBG1ErrorBlock)error;


BG1 modifies the notification name and the notification is defined in the BGMacrofile.h file：

old macros：      BG1ConnectNoti              BG1DisConnectNoti           MicroPhoneEnableBG1

new macros：    kNotificationNameAudioDeviceInsert      kNotificationNameBG1DidDisConnect   kNotificationNameNeedAudioPermission


5. Update the commandSendBottleID method of BG5 to fix the problem that bottleID can't parse correctly in 32-bit iOS devices, and the incoming type is changed from NSNumber to long long

6. Modified BP interface spelling error new exposed interface, pregress changed to progress

Release Date: 2017-10-20
```
### 10. V2.1.4
```
Description:

1. To optimize the HS5 code
2. Add the SDKInfo class to get the current version of SDK and UUID 
3. add Log statistics of connection failure
4. To optimize the BG1 connection

Release Date: 2017-11-28
```

