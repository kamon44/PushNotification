# PushNotification
  * App.js
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
     from './src/utils/Pushnotification_helper.js';

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
