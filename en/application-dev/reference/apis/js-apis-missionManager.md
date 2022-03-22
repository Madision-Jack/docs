# missionManager


> **NOTE**
> The initial APIs of this module are supported since API version 8.


Provides mission management. You can use the APIs to lock, unlock, and clear missions, and switch a mission to the foreground.


## Modules to Import


```
import missionManager from '@ohos.application.missionManager'
```


## missionManager.registerMissionListener

function registerMissionListener(listener: MissionListener): number;

Registers a listener to observe the mission status.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | listener | MissionListener | Yes| Listener to register.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | number | Returns the index of the listener, which is created by the system and allocated when the mission status listener is registered. Each listener has a unique index.|

**Example**

  ```js
  var listener =  {
  	onMissionCreated: this.onMissionCreatedCallback,
  	onMissionDestroyed: this.onMissionDestroyedCallback,
  	onMissionSnapshotChanged: this.onMissionSnapshotChangedCallback,
  	onMissionMovedToFront: this.onMissionMovedToFrontCallback
  };
  console.log("registerMissionListener")
  var listenerid = missionManager.registerMissionListener(listener);

  ```


## missionManager.unregisterMissionListener

function unregisterMissionListener(listenerId: number, callback: AsyncCallback&lt;void&gt;): void;

Unregisters a mission status listener. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | listenerId | number | Yes| Index of the mission status listener to unregister. Each listener has a unique index, which is returned by **registerMissionListener**.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Example**

  ```js
  var listener =  {
    onMissionCreated: this.onMissionCreatedCallback,
    onMissionDestroyed: this.onMissionDestroyedCallback,
    onMissionSnapshotChanged: this.onMissionSnapshotChangedCallback,
    onMissionMovedToFront: this.onMissionMovedToFrontCallback
  };
  console.log("registerMissionListener")
  var listenerid = missionManager.registerMissionListener(listener);

  missionManager.unregisterMissionListener(listenerid, (error) => {
    console.log("unregisterMissionListener");
  })
  ```


## missionManager.unregisterMissionListener

function unregisterMissionListener(listenerId: number): Promise&lt;void&gt;;

Unregisters a mission status listener. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | listenerId | number | Yes| Index of the mission status listener to unregister. Each listener has a unique index, which is returned by **registerMissionListener**.|

**Example**

  ```js
  var listener =  {
      onMissionCreated: this.onMissionCreatedCallback,
      onMissionDestroyed: this.onMissionDestroyedCallback,
      onMissionSnapshotChanged: this.onMissionSnapshotChangedCallback,
      onMissionMovedToFront: this.onMissionMovedToFrontCallback
    };
    console.log("registerMissionListener")
    var listenerid = missionManager.registerMissionListener(listener);

    await missionManager.unregisterMissionListener(listenerid).catch(function (err){
      console.log(err);
    });
  ```


## missionManager.getMissionInfo

function getMissionInfo(deviceId: string, missionId: number, callback: AsyncCallback&lt;MissionInfo&gt;): void;

Obtains the information of a given mission. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;MissionInfo&gt; | Yes| Callback used to return the mission information obtained.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.getMissionInfo("", allMissions[0].missionId, (error, mission) => {
  	console.log("getMissionInfo is called, error.code = " + error.code)
  	console.log("mission.missionId = " + mission.missionId);
  	console.log("mission.runningState = " + mission.runningState);
  	console.log("mission.lockedState = " + mission.lockedState);
  	console.log("mission.timestamp = " + mission.timestamp);
  	console.log("mission.label = " + mission.label);
  	console.log("mission.iconPath = " + mission.iconPath);
  }
  ```


## missionManager.getMissionInfo

function getMissionInfo(deviceId: string, missionId: number): Promise&lt;MissionInfo&gt;;

Obtains the information of a given mission. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | [MissionInfo](js-apis-application-MissionInfo.md) | Promise used to return the mission information obtained.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  var mission = await missionManager.getMissionInfo("", id).catch(function (err){
      console.log(err);
  });
  ```


## missionManager.getMissionInfos

function getMissionInfos(deviceId: string, numMax: number, callback: AsyncCallback&lt;Array&lt;MissionInfo&gt;&gt;): void;

Obtains information of all missions. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | numMax | number | Yes| Maximum number of missions whose information can be obtained.|
  | callback | AsyncCallback&lt;Array&lt;[MissionInfo](js-apis-application-MissionInfo.md)&gt;&gt; | Yes| Callback used to return the array of mission information obtained.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.getMissionInfos("", 10, (error, missions) => {
      console.log("getMissionInfos is called, error.code = " + error.code);
      console.log("size = " + missions.length);
      console.log("missions = " + JSON.stringify(missions));
  })
  ```


## missionManager.getMissionInfos

function getMissionInfos(deviceId: string, numMax: number): Promise&lt;Array&lt;MissionInfo&gt;&gt;;

Obtains information of all missions. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | numMax | number | Yes| Maximum number of missions whose information can be obtained.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | Array&lt;MissionInfo&gt; | Promise used to return the array of mission information obtained.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  var allMissions = await missionManager.getMissionInfos("", 10).catch(function (err){
      console.log(err);
  });
  ```


## missionManager.getMissionSnapShot

function getMissionSnapShot(deviceId: string, missionId: number, callback: AsyncCallback&lt;MissionSnapshot&gt;): void;

Obtains the snapshot of a given mission. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;[MissionSnapshot](js-apis-application-MissionSnapshot.md)&gt; | Yes| Callback used to return the snapshot information obtained.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.getMissionInfos("", 10, (error, missions) => {
    console.log("getMissionInfos is called, error.code = " + error.code);
    console.log("size = " + missions.length);
    console.log("missions = " + JSON.stringify(missions));
    var id = missions[0].missionId;

    missionManager.getMissionSnapShot("", id, (error, snapshot) => {
  	console.log("getMissionSnapShot is called, error.code = " + error.code);
  	console.log("bundleName = " + snapshot.ability.bundleName);
  })
  })
  ```


## missionManager.getMissionSnapShot

function getMissionSnapShot(deviceId: string, missionId: number): Promise&lt;MissionSnapshot&gt;;

Obtains the snapshot of a given mission. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | deviceId | string | Yes| Device ID. It is a null string by default for the local device.|
  | missionId | number | Yes| Mission ID.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | MissionSnapshot | Promise used to return the snapshot information obtained.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  var allMissions = await missionManager.getMissionInfos("", 10).catch(function (err){
    console.log(err);
  });
  console.log("size = " + allMissions.length);
  console.log("missions = " + JSON.stringify(allMissions));
  var id = allMissions[0].missionId;
  var snapshot = await missionManager.getMissionSnapShot("", id).catch(function (err){
    console.log(err);
  });
  ```


## missionManager.lockMission

function lockMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void;

Locks a given mission. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.getMissionInfos("", 10, (error, missions) => {
    console.log("getMissionInfos is called, error.code = " + error.code);
    console.log("size = " + missions.length);
    console.log("missions = " + JSON.stringify(missions));
    var id = missions[0].missionId;

    missionManager.lockMission(id).then(() => {
  	console.log("lockMission is called ");
  });
  });
  ```


## missionManager.lockMission

function lockMission(missionId: number): Promise&lt;void&gt;;

Locks a given mission. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  var allMissions = await missionManager.getMissionInfos("", 10).catch(function (err){
    console.log(err);
  });
  console.log("size = " + allMissions.length);
  console.log("missions = " + JSON.stringify(allMissions));
  var id = allMissions[0].missionId;

  await missionManager.lockMission(id).catch(function (err){
      console.log(err);
  });
  ```


## missionManager.unlockMission

function unlockMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void;

Unlocks a given mission. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.getMissionInfos("", 10, (error, missions) => {
    console.log("getMissionInfos is called, error.code = " + error.code);
    console.log("size = " + missions.length);
    console.log("missions = " + JSON.stringify(missions));
    var id = missions[0].missionId;

    missionManager.unlockMission(id).then(() => {
  	console.log("unlockMission is called ");
  });
  });
  ```


## missionManager.unlockMission

function unlockMission(missionId: number): Promise&lt;void&gt;;

Unlocks a given mission. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  var allMissions = await missionManager.getMissionInfos("", 10).catch(function (err){
    console.log(err);
  });
  console.log("size = " + allMissions.length);
  console.log("missions = " + JSON.stringify(allMissions));
  var id = allMissions[0].missionId;

  await missionManager.lockMission(id).catch(function (err){
      console.log(err);
  });
  await missionManager.unlockMission(id).catch(function (err){
      console.log(err);
  });
  ```


## missionManager.clearMission

function clearMission(missionId: number, callback: AsyncCallback&lt;void&gt;): void;

Clears a given mission, regardless of whether it is locked. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.getMissionInfos("", 10, (error, missions) => {
    console.log("getMissionInfos is called, error.code = " + error.code);
    console.log("size = " + missions.length);
    console.log("missions = " + JSON.stringify(missions));
    var id = missions[0].missionId;

    missionManager.clearMission(id).then(() => {
  	console.log("clearMission is called ");
  });
  });
  ```


## missionManager.clearMission

function clearMission(missionId: number): Promise&lt;void&gt;;

Clears a given mission, regardless of whether it is locked. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  var allMissions = await missionManager.getMissionInfos("", 10).catch(function (err){
    console.log(err);
  });
  console.log("size = " + allMissions.length);
  console.log("missions = " + JSON.stringify(allMissions));
  var id = allMissions[0].missionId;

  await missionManager.clearMission(id).catch(function (err){
    console.log(err);
  });
  ```


## missionManager.clearAllMissions

function clearAllMissions(callback: AsyncCallback&lt;void&gt;): void;

Clears all unlocked missions. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.clearAllMissions().then(() => {
    console.log("clearAllMissions is called ");
  });
  ```


## missionManager.clearAllMissions

function clearAllMissions(): Promise&lt;void&gt;;

Clears all unlocked missions. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'
  await missionManager.clearAllMissions().catch(function (err){
    console.log(err);
  });
  ```


## missionManager.moveMissionToFront

function moveMissionToFront(missionId: number, callback: AsyncCallback&lt;void&gt;): void;

Switches a given mission to the foreground. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.getMissionInfos("", 10, (error, missions) => {
    console.log("getMissionInfos is called, error.code = " + error.code);
    console.log("size = " + missions.length);
    console.log("missions = " + JSON.stringify(missions));
    var id = missions[0].missionId;

    missionManager.moveMissionToFront(id).then(() => {
  	console.log("moveMissionToFront is called ");
  });
  });
  ```


## missionManager.moveMissionToFront

function moveMissionToFront(missionId: number, options: StartOptions, callback: AsyncCallback&lt;void&gt;): void;

Switches a given mission to the foreground, with the startup parameters for the switch specified, such as the window mode and device ID. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | options | StartOptions | Yes| Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  missionManager.getMissionInfos("", 10, (error, missions) => {
    console.log("getMissionInfos is called, error.code = " + error.code);
    console.log("size = " + missions.length);
    console.log("missions = " + JSON.stringify(missions));
    var id = missions[0].missionId;

    missionManager.moveMissionToFront(id,{windowMode : 101}).then(() => {
  	console.log("moveMissionToFront is called ");
    });
  });
  ```


## missionManager.moveMissionToFront

function moveMissionToFront(missionId: number, options?: StartOptions): Promise&lt;void&gt;;

Switches a given mission to the foreground. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | missionId | number | Yes| Mission ID.|
  | options | StartOptions | No| Startup parameters, which are used to specify the window mode and device ID for switching the mission to the foreground.|

**Example**

  ```js
  import missionManager from '@ohos.application.missionManager'

  var allMissions = await missionManager.getMissionInfos("", 10).catch(function (err){
    console.log(err);
  });
  console.log("size = " + allMissions.length);
  console.log("missions = " + JSON.stringify(allMissions));
  var id = allMissions[0].missionId;

  await missionManager.moveMissionToFront(id).catch(function (err){
    console.log(err);
  });
  ```