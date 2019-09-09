# video-call

<?xml version="1.0" encoding="utf-8"?>
<s:Application xmlns:fx="http://ns.adobe.com/mxml/2009" xmlns:s="library://ns.adobe.com/flex/spark" xmlns:cs="AfcsNameSpace" currentState="logon" fontSize="28">
 
    <fx:Script>
        [Bindable] private var roomURL:String = "http://connectnow.acrobat.com/YOUR_ROOM_NAME";
 
        protected function connect():void {
            auth.userName = userName.text;
            currentState = "default";
            session.login();
        }
    </fx:Script>
 
    <s:states>
        <s:State name="default"/>
        <s:State name="logon"/>
    </s:states>
 
    <fx:Declarations>
        <cs:AdobeHSAuthenticator id="auth"/>
    </fx:Declarations>
 
    <s:TextInput id="userName" includeIn="logon" top="200" horizontalCenter="0"/>
    <s:Button label="Connect" click="connect()" includeIn="logon" top="250" horizontalCenter="0" height="50" width="150"/>
 
    <cs:ConnectSessionContainer id="session" roomURL="{roomURL}" authenticator="{auth}" autoLogin="false" width="100%" height="100%" includeIn="default">
        <cs:WebCamera top="10" left="10" bottom="10" right="10"/>
    </cs:ConnectSessionContainer>
 
</s:Application>
