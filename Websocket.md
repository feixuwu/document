# UEWebsocket
unreal engine 4 websocket plugin(support ssl) for both c++ and blueprint developer.

This plugin is for unreal engine 4 c++ and blueprint developers, you can easily use c++ or blueprint
 to connect to remote server and send receive messages.


# Supported Platform
★ 1. Win64

★ 3. Android

★ 4. IOS

★ 7. Win32


# Usage

## Blueprint

★ Connect To Server

   ![ScreenShot](docs/connect.PNG)
   
★ Bind Event, Send And Receive Data

   ![ScreenShot](docs/bind.PNG)
   
★ ssl support

   this plugin support wss, it will automatic create ca file, the ca content is an array in WebSocketCA.cpp file.
   
## C++
Please first check the demo project:[demo projejct](https://drive.google.com/file/d/1iChDYrPc-pqy9hNx1v6IWmksjMnbwDcc/view?usp=sharing)

★ Connect To Server(C++)
   1. define a websocket object in your class
   ```
      UPROPERTY(BlueprintReadOnly)
	     UWebSocketBase* mDemoSocket;
   ```

   2. in cpp function, create socket and bind event
   ```
 bool connectFail = false;
	mDemoSocket = UWebSocketBlueprintLibrary::Connect("wss://echo.websocket.org", connectFail);

	if (connectFail)
	{
		OnConnectError(TEXT("connect fail, please check url format") );
		mDemoSocket = nullptr;
		return;
	}

	
	mDemoSocket->OnConnectComplete.AddDynamic(this, &ADemoGameMode::OnConnectComplete);
	mDemoSocket->OnConnectError.AddDynamic(this, &ADemoGameMode::OnConnectError);
	mDemoSocket->OnClosed.AddDynamic(this, &ADemoGameMode::OnConnectionClose);
	mDemoSocket->OnReceiveData.AddDynamic(this, &ADemoGameMode::OnDataReceive);
   ```

★ Send Data(C++)
  ```
  mDemoSocket->SendText(TEXT("C++ Hello World"));
  ```

★ Reconnect(C++)
  ```
  void ADemoGameMode::CppReconnectShowCase()
{
	if (mDemoSocket != nullptr)
	{
		mDemoSocket->Close();
		mDemoSocket = nullptr;
	}

	bool connectFail = false;
	mDemoSocket = UWebSocketBlueprintLibrary::Connect("wss://echo.websocket.org", connectFail);

	if (connectFail)
	{
		OnConnectError(TEXT("connect fail, please check url format") );
		mDemoSocket = nullptr;
		return;
	}

	
	mDemoSocket->OnConnectComplete.AddDynamic(this, &ADemoGameMode::OnConnectComplete);
	mDemoSocket->OnConnectError.AddDynamic(this, &ADemoGameMode::OnConnectError);
	mDemoSocket->OnClosed.AddDynamic(this, &ADemoGameMode::OnConnectionClose);
	mDemoSocket->OnReceiveData.AddDynamic(this, &ADemoGameMode::OnDataReceive);
}
  ```
     
# tutorial video:
[![how to use websocket](https://i9.ytimg.com/vi/E3pIdmwvLl0/mq2.jpg?sqp=CPSikvgF&rs=AOn4CLDjrM5mSKD3TIT1qFW9vCvBeNG4dg)](https://youtu.be/E3pIdmwvLl0)
   
