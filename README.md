# Firebase-ESP8266

Google's Firebase real time database - ESP8266 library for Arduino

This library provides ESP8266 to complete working with Google's Firebase database through the REST API. 

The library was test and work well with ESP8266s based module.

Copyright (c) 2019 K. Suwatchai (Mobizt).

## Tested Devices

This library works well in the following tested devices.

 * Wemos D1 Mini
 * NodeMCU
 
## Features
Complete Firebase's REST API requests.
Able to PUT, POST, STREAM, PATCH, DELETE data using set, push, stream, update and delete functions.
Support integer, float, String and raw JSON String data types.
Able to set multiple stream path (require more RAM) and single stream path (swap between stream and other set/get/push).
No certificate or fingerprint required as default.

**Supported functions**

```c++
   /**
   * The Firebase's credentials initialization.
   * \param host - Your Firebase database project host i.e. Your_ProjectID.firebaseio.com.
   * \param auth - Your database secret.
   */
    void begin(const String host, const String auth);
	
   /**
   * Auto reconnect WiFi when connection lost during request.
   * \param reconnect - True for auto reconnect.
   */
    void reconnectWiFi(bool reconnect);
	
   /**
   * Check for the existence of node path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be checked.
   */
    bool pathExist(FirebaseData &dataObj, const String path);
	
   /**
   * Post or append/create new child node integer data.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Parent node path to be append.
   * \param intValue - Integer value to be append.
   * \return The operating status. True for success operation and False for failed operation.
   * To get new push node name, call FirebaseData.pushName().
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   */
    bool pushInt(FirebaseData &dataObj, const String path, int intValue);
	
   /**
   * Post or append/create new child node float data.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Parent node path to be append.
   * \param floatValue - Float value to be append.
   * \return The operating status. TTrue for success operation and False for failed operation.
   * To get new push node name, call FirebaseData.pushName().
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   */
    bool pushFloat(FirebaseData &dataObj, const String path, float floatValue);
	
   /**
   * Post or append/create new child node String data.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Parent node path to be append.
   * \param StringValue - String value to be append.
   * \return The operating status. True for success operation and False for failed operation.
   * To get new push node name, call FirebaseData.pushName().
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   */
    bool pushString(FirebaseData &dataObj, const String path, const String stringValue);
	
   /**
   * Post or append/create new node JSON data.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Parent node path to be append.
   * \param jsonString - Raw JSON String to be append (should be correct JSONformat).
   * \return The operating status. True for success operation and False for failed operation.
   * To get new push node name, call FirebaseData.pushName().
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   */
    bool pushJSON(FirebaseData &dataObj, const String path, const String jsonString);
	
   /**
   * Put or set integer data to child node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be set value.
   * \param intValue - Integer value to be set.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual payload data from operation, call FirebaseData.intData().
   */
    bool setInt(FirebaseData &dataObj, const String path, int intValue);
	
   /**
   * Put or set float data to node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be set value.
   * \param floatValue - Float value to be set.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual payload data from operation, call FirebaseData.floatData().
   */
    bool setFloat(FirebaseData &dataObj, const String path, float floatValue);
	
   /**
   * Put or set String data to child node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be set value.
   * \param stringValue - String value to be set.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual payload data from operation, call FirebaseData.stringData().
   */
    bool setString(FirebaseData &dataObj, const String path, const String stringValue);
	
   /**
   * Put or set JSON data to child node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be set value.
   * \param jsonString - Raw JSON string to be set (should be correct JSONformat).
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual payload data from operation, call FirebaseData.jsonData().
   */
    bool setJSON(FirebaseData &dataObj, const String path, const String jsonString);
	
   /**
   * Patch or update JSON data to child node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be update the value.
   * \param jsonString - Raw JSON string to be update (should be correct JSONformat contains key/value pairs).
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual payload data from operation, call FirebaseData.jsonData().
   */
    bool updateNode(FirebaseData &dataObj, const String path, const String jsonString);
	
   /**
   * Get the integer data from child node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be read the value.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual return integer data, call FirebaseData.intData(). If the data at node path is float type, 
   * the return data will be rounded  and if the data at node path is other types than integer or float, 
   * the return integer data will be zero.
   */
    bool getInt(FirebaseData &dataObj, String path);
	
   /**
   * Get the float data from child node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be read the value.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual return float data, call FirebaseData.floatData(). If the data at node path is other types than float or integer, 
   * the return float data will be zero.
   */
    bool getFloat(FirebaseData &dataObj, String path);
	
   /**
   * Get the String data from child node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be read the value.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual return String data, call FirebaseData.stringData(). If the data at node path is other types than String, 
   * the return String data will be empty string.
   */
    bool getString(FirebaseData &dataObj, String path);
	
   /**
   * Get the raw JSON String data from child node at the specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be read the value.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   * To get actual data type, call FirebaseData.dataType().
   * To get actual return raw JSON String data, call FirebaseData.jsonData(). If the data at node path is other types than JSON, 
   * the return String data will be empty string.
   */
    bool getJSON(FirebaseData &dataObj, String path);
	
   /**
   * Delete the node at specified path. The entire children nodes also deleted.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Node path to be deleted.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   */
    bool deleteNode(FirebaseData &dataObj, const String path);
	
   /**
   * Begin monitoring the change of data at node and its children at specified path.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \param path - Parent node path to be monitor.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   */
    bool beginStream(FirebaseData &dataObj, const String path);
	
   /**
   * Read the stream event data at specified path. Should be called in loop or loop tasks after begin stream called in setup().
   * \param dataObj - FirebaseData object that requred for internal works.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   */
    bool readStream(FirebaseData &dataObj);
	
   /**
   * End the stream operation at specified path. Can be start stream again by call beginStream once.
   * \param dataObj - FirebaseData object that requred for internal works.
   * \return The operating status. True for success operation and False for failed operation.
   * To get error reason, call FirebaseData.errorReason().
   */
    bool endStream(FirebaseData &dataObj);
	


 For FirebaseData object call

	
   
   /**
   * Return the actual data type that return as payload from get/set/push calls.
   * \return The data type String (int, float, string and json).
   */
    String dataType();
	
   /**
   * Return the current stream path.
   * \return The path String.
   */
    String streamPath();
	
   /**
   * Return the current data path.
   * \return The current path String from get/set/push calls or current changed data path from stream call.
   */
    String dataPath();
	
   /**
   * Return the error reason String from current call.
   * \return The error String.
   */
    String errorReason();
	
   /**
   * Return the ineger data from current get/set/push and stream calls.
   * \return The payload or returned integer data.
   */
    int intData();
	
   /**
   * Return the float data from current get/set/push and stream calls.
   * \return The payload or returned float data.
   */
    float floatData();
	
   /**
   * Return the String data from current get/set/push and stream calls.
   * \return The payload or returned String data.
   */
    String stringData();
	
   /**
   * Return the raw JSON String data from current get/set/push and stream calls.
   * \return The payload or returned raw JSON String data.
   */
    String jsonData();
	
   /**
   * Return the new created child node name (String) from push call.
   * \return The String of new append node name.
   */
    String pushName();
	
   /**
   * Check the current FirebaseData object is currently work with stream.
   * \return The status. True for being stream.
   */
    bool isStream();
	
   /**
   * Check the current FirebaseData object is currently connected to server.
   * \return The connected status. True for connected.
   */
    bool httpConnected();
	
   /**
   * Check the current stream connection of FirebaseData object is timeout from server (30 sec is default).
   * Nothing to do when timeout, the stream is automatic resume.
   * \return The timeout status. True for timeout occurred.
   */
    bool streamTimeout();
	
   /**
   * Check the data is available from get/set/push calls.
   * \return The data available status. True for data is available.
   */
    bool dataAvailable();
	
   /**
   * Check the update/changes data is available from current stream  of FirebaseData object.
   * \return The stream data available status. True for stream data is available.
   */
    bool streamAvailable();
	
   /**
   * Check the matching between data type being call and the server return data type.
   * \return The mismatch status. True for mismatch.
   */
    bool mismatchDataType();
	
   /**
   * Check the http code return from all calls.
   * \return The integer data of http response.
   */
    int httpCode();
	
   /**
   * Check overflow of the return data buffer.
   * \return The overflow status. True for overflow. If overflow change the defined value in FirebaseESP8266.h
   * #define FIREBASE_RESPONSE_SIZE xxxx
   * #define FIREBASE_DATA_SIZE xxxx
   */
   bool bufferOverflow();

```


## Usages

```c++

See the examples

```