# DcloudDebugPush
DCloud 个推 unipush 推送调试基座


你需要使用正式签名运行APP，来保证个推正常运行



            android {
                  signingConfigs {
            //        第三方sdk调试需要 正式签名 运行
                    release {
                        storeFile file('D:\\2.hydcode\\zcar-app\\unpackage\\build\\zcar-app.jks')
                        storePassword '证书密码'
                        keyAlias = '证书别名'
                        keyPassword '密钥密码'
                    }
                }

                ......
            }

设置你自己的 applicationId "xxxxxxxxxxxxxx"  （in  app->build.gradle）

设置你的包名（in AndroidManifest.xml） 

  <manifest xmlns:android="http://schemas.android.com/apk/res/android"
     package="your package name"    > 
    
    <uses-permission android:name="getui.permission.GetuiService.your package name"/>
    <permission android:name="getui.permission.GetuiService.your package name" android:protectionLevel="normal"/>
    
     <application>
    
       ..........
       
       
         设置你个推信息   
        <!-- 个推配置        -->
        <!-- uniPush 配置      -->
        <meta-data android:name="PUSH_APPID" android:value="your appid"/>
        <meta-data android:name="PUSH_APPSECRET" android:value="your appsecret"/>
        <meta-data android:name="PUSH_APPKEY" android:value="your appkey"/>
       
     
          <receiver android:name="io.dcloud.feature.apsGt.GTNotificationReceiver">
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED"/>
                <action android:name="your package name.__CREATE_NOTIFICATION"/>
                <action android:name="your package name.__REMOVE_NOTIFICATION"/>
                <action android:name="your package name.__CLEAR_NOTIFICATION"/>
                <action android:name="your package name.__CLILK_NOTIFICATION"/>
            </intent-filter>
        </receiver>
     </application>
     
    
   </manifest>
   
   你需要设置 5+app id 来保证基座运行正常
   
   assets->apps->5+app id ->www-> you html file
   assets->data->dcloud_control(文件内) 
    
    <hbuilder version="1.9.9.74103">
    <apps>
        <app appid="your 5+app id" appver=""/>
    </apps>
    </hbuilder>
    
    

   使用release构建 
   Build Variants (在Android studio 做下脚  favorites 上面 )
   
   Module  Active Build Variant
   app     release 
   
   
   
      
    

