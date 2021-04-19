# react-native-aws-freertos

React native aws freertos bridge

## Installation

```sh
npm install react-native-aws-freertos
```

## Usage

```js
import AwsFreertos from "react-native-aws-freertos";

// ...
AwsFreertos.getConnectedDeviceAvailableNetworks(deviceMacAddress);
const eventEmitter = new NativeEventEmitter(NativeModules.AwsFreertos);

const wifiListEvent = eventEmitter.addListener(
    eventKeys.DID_LIST_NETWORK,
    (network: WifiInfo) => {
      console.log(network)
    }
);
```

## Available methods
```ts
type AwsFreertosType = {
  startScanBtDevices(): void;
  stopScanBtDevices(): void;
  requestBtPermissions(): Promise<any>;
  connectDevice(macAddress: string): Promise<any>;
  disconnectDevice(macAddress: string): Promise<any>;
  disconnectNetworkOnConnectedDevice(macAddress: string, index: number): Promise<any>;
  saveNetworkOnConnectedDevice(
    macAddress: string,
    bssid: string,
    pw: string
  ): Promise<any>;
  getConnectedDeviceAvailableNetworks(macAddress: string): Promise<WifiInfo[]>;
  getConnectedDeviceSavedNetworks(macAddress: string): Promise<WifiInfo[]>;
  getGattCharacteristicsFromServer(
    macAddress: string,
    serviceUuidString: string
  ): void;
};
```

## Events
```js
export const events = {
  // Bluetooth events
  DID_UPDATE_BLE_POWER_STATE: 'DID_UPDATE_BLE_POWER_STATE',
  DID_DISCONNECT_DEVICE: 'DID_DISCONNECT_DEVICE',
  DID_DISCOVERED_DEVICE: 'DID_DISCOVERED_DEVICE',
  DID_CONNECT_DEVICE: 'DID_CONNECT_DEVICE',
  DID_FAIL_TO_CONNECT_DEVICE: 'DID_FAIL_TO_CONNECT_DEVICE',
  DID_READ_CHARACTERISTIC_FROM_SERVICE: 'DID_READ_CHARACTERISTIC_FROM_SERVICE',

  // Wifi events of paired up device
  DID_LIST_NETWORK: 'DID_LIST_NETWORK',
  DID_SAVE_NETWORK: 'DID_SAVE_NETWORK',
  ERROR_SAVE_NETWORK: 'ERROR_SAVE_NETWORK',
  DID_EDIT_NETWORK: 'DID_EDIT_NETWORK',
  DID_DELETE_NETWORK: 'DID_DELETE_NETWORK',
};
```


## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT
