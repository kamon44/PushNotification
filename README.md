# PushNotification
# Coding
# App.js
```
import React from 'react';
import {useEffect}from 'react';
import {
  SafeAreaView,
  ScrollView,
  StatusBar,
  StyleSheet,
  Text,
  useColorScheme,
  View,
} from 'react-native';

import {requestUserPermission,NotificationListner}
 from './เรียกไฟล์ที่สร้างขึ้น';
 
  const App = () => {
    useEffect(()=>{
      requestUserPermission();
      NotificationListner();
    },[])

return(
<View style={{alignSelf:"center",fiex:1,justifycontent:"center"}}>
<Text style={{fontWeight:"bold"}}>Push Notification Tester</Text>
</View>
);

};
export default App;

const styles = StyleSheet.create({
  sectionContainer: {
    marginTop: 32,
    paddingHorizontal: 24,
  },
  sectionTitle: {
    fontSize: 24,
    fontWeight: '600',
  },
  sectionDescription: {
    marginTop: 8,
    fontSize: 18,
    fontWeight: '400',
  },
  highlight: {
    fontWeight: '700',
  },
});
```

# ProjectName

```
import messaging from '@react-native-firebase/messaging';
import AsyncStorage from '@react-native-async-storage/async-storage';

export async function requestUserPermission() {
  const authStatus = await messaging().requestPermission();
  const enabled =
    authStatus === messaging.AuthorizationStatus.AUTHORIZED ||
    authStatus === messaging.AuthorizationStatus.PROVISIONAL;

  if (enabled) {
    console.log('Authorization status:', authStatus);
    GetFCMToke();
  }
}

async function GetFCMToke(){
let fcmtoken=await AsyncStorage.getItem("fcmtoken");
console.log(fcmtoken,"old token");
if(!fcmtoken){

  try{
    const fcmtoken=await messaging().getToken();
    if(fcmtoken){

        console.log(fcmtoken,"new token");
        await AsyncStorage.setItem("fcmtoken",fcmtoken);
        }
    }
    catch(error){
    console.log(error,"error in fcmtoken");
    }

}

}
export const NotificationListner=()=>{
    // Assume a message-notification contains a "type" property in the data payload of the screen to open

    messaging().onNotificationOpenedApp(remoteMessage => {
        console.log(
          'Notification caused app to open from background state:',
          remoteMessage.notification,
        );
      });

      // Check whether an initial notification is available
    messaging()
    .getInitialNotification()
    .then(remoteMessage => {
      if (remoteMessage) {
        console.log(
          'Notification caused app to open from quit state:',
          remoteMessage.notification,
        );
      }
    });

    messaging().onMessage(async remoteMessage=>{
        console.log("notification on froground state........",remoteMessage);
    })
}
```

# Index.js

```
import {AppRegistry} from 'react-native';
import App from './App';
import {name as appName} from './app.json';
import messaging from '@react-native-firebase/messaging';

messaging().setBackgroundMessageHandler(async remoteMessage => {
    console.log('Message handled in the background!', remoteMessage);
  });

AppRegistry.registerComponent(appName, () => App);
```
# รายชื่อสมาชิกในกลุ่ม
63100218 กมลวรรณ พลสุวรรณ
63102164 ชัยนัฐ อินทรพฤกษา
63105712 เบญจรัตน์ ดาราสิชฌน์
63106868 พรรณวษา ศรีสุข
63109854 วิษณุ มณีวรรณ
63110548 ศิวกร ทันยุภักดิ์
63110688 ศุภสิน จันทร์ไหม
63111256 สุญาดา เกษถนอม
63112320 อรัญญา วิชัยกุล
63113195 ธนายุต สังข์สิงห์
63118590 นูรอิลมีย์ ฮูลูสาและ
63121230 ธนวัฒน์ เพ่งพินิจ
63121248 ธนากร ขุนณรงค์
63122964 ศานติกร ทองนุ้ย
