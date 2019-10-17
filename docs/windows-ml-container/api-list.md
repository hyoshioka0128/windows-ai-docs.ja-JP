---
title: API の一覧
description: Windows ML コンテナーで使用するためにホワイトリストに登録されている Api を調べる
ms.date: 10/14/2019
ms.topic: article
keywords: windows 10, windows ml container, container, iot, edge
ms.localizationpriority: medium
ms.openlocfilehash: 6567256c71feb0f110cfac71ed239efac3037add
ms.sourcegitcommit: e08b8ae92e48c1b82bb6f94fefcb32cd817453d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443006"
---
# <a name="api-list"></a>API の一覧

[OneCore の包括的なライブラリ](https://docs.microsoft.com/windows/win32/apiindex/umbrella-lib-onecore)によってエクスポートされた api は、Windows ML コンテナーのネイティブアプリケーションで使用できます。

Windows ML コンテナーのサイズが小さいため、コンテナーイメージで使用できるのは WinRT Api のサブセットのみです。  次の一覧は、基本 OS イメージに含まれる型を入念に一覧表示することを目的としています。  含まれていない型が必要な場合は、winmlcfb@microsoft.com をメールで送信してください。

## <a name="windowsai"></a>Windows.AI

### <a name="windowsaimachinelearninghttpsdocsmicrosoftcomuwpapiwindowsaimachinelearning"></a>[Windows.AI.MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning)

ILearningModelFeatureDescriptor </br> ILearningModelFeatureValue </br> ILearningModelOperatorProvider </br> ITensor </br> ImageFeatureDescriptor </br> ImageFeatureValue </br> LearningModel </br> LearningModelBinding </br> LearningModelDevice </br> LearningModelDeviceKind </br> LearningModelEvaluationResult </br> LearningModelFeatureKind </br> LearningModelSession </br> LearningModelSessionOptions </br> MachineLearningContract </br> MapFeatureDescriptor </br> SequenceFeatureDescriptor </br> TensorBoolean </br> TensorDouble </br> TensorFeatureDescriptor </br> TensorFloat </br> TensorFloat16Bit </br> TensorInt16Bit </br> TensorInt32Bit </br> TensorInt64Bit </br> TensorInt8Bit </br> TensorKind </br> TensorString </br> TensorUInt16Bit </br> TensorUInt32Bit </br> TensorUInt64Bit </br> TensorUInt8Bit

## <a name="windowsapplicationmodel"></a>Windows.ApplicationModel

### <a name="windowsapplicationmodelbackgroundhttpsdocsmicrosoftcomuwpapiwindowsapplicationmodelbackground"></a>[Windows.ApplicationModel.Background](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background)

DeviceWatcherTrigger </br> IBackgroundTrigger

## <a name="windowsdata"></a>Windows.Data

### <a name="windowsdatahtmlhttpsdocsmicrosoftcomuwpapiwindowsdatahtml"></a>[Windows. データ .Html](https://docs.microsoft.com/uwp/api/Windows.Data.Html)

HtmlUtilities

### <a name="windowsdatajsonhttpsdocsmicrosoftcomuwpapiwindowsdatajson"></a>[Windows. Data. Json](https://docs.microsoft.com/uwp/api/Windows.Data.Json)

IJsonValue </br> JsonArray </br> JsonError </br> JsonErrorStatus </br> JsonObject </br> JsonValue </br> JsonValueType

### <a name="windowsdatatexthttpsdocsmicrosoftcomuwpapiwindowsdatatext"></a>[Windows.Data.Text](https://docs.microsoft.com/uwp/api/Windows.Data.Text)

AlternateNormalizationFormat </br> AlternateWordForm </br> SelectableWordSegment </br> SelectableWordSegmentsTokenizingHandler </br> SelectableWordsSegmenter </br> SemanticTextQuery </br> TextConversionGenerator </br> TextPhoneme </br> TextPredictionGenerator </br> TextPredictionOptions </br> TextReverseConversionGenerator </br> TextSegment </br> UnicodeCharacters </br> UnicodeGeneralCategory </br> UnicodeNumericType </br> WordSegment </br> WordSegmentsTokenizingHandler </br> WordsSegmenter

### <a name="windowsdataxmldomhttpsdocsmicrosoftcomuwpapiwindowsdataxmldom"></a>[Windows. Data. .Xml. Dom](https://docs.microsoft.com/uwp/api/Windows.Data.Xml.Dom)

DtdEntity </br> DtdNotation </br> IXmlCharacterData </br> IXmlNode </br> IXmlNodeSelector </br> IXmlNodeSerializer </br> IXmlText br > NodeType </br> XmlAttribute </br> Xmlcdatas </br> XmlComment </br> Xml </br> XmlDocumentFragment </br> XmlDocumentType </br> XmlDomImplementation </br> XmlElement </br> XmlEntityReference </br> XmlLoadSettings </br> XmlNamedNodeMap </br> XmlNodeList </br> XmlProcessingInstruction </br> XmlText

### <a name="windowsdataxmlxslhttpsdocsmicrosoftcomuwpapiwindowsdataxmlxsl"></a>[Windows. .Xml. .Xsl](https://docs.microsoft.com/uwp/api/Windows.Data.Xml.Xsl)

XsltProcessor

## <a name="windowsdevices"></a>Windows.Devices

### <a name="windowsdeviceshttpsdocsmicrosoftcomuwpapiwindowsdevices"></a>[Windows. デバイス](https://docs.microsoft.com/uwp/api/windows.devices)

ILowLevelDevicesAggregateProvider </br> LowLevelDevicesAggregateProvider </br> Lowlevelデバイスコントローラー

### <a name="windowsdevicesadchttpsdocsmicrosoftcomuwpapiwindowsdevicesadc"></a>[Windows. デバイス. Adc](https://docs.microsoft.com/uwp/api/windows.devices.adc)

AdcChannel </br> AdcChannelMode </br> AdcController

### <a name="windowsdevicesadcproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicesadcprovider"></a>[Windows. デバイス. Adc. プロバイダー](https://docs.microsoft.com/uwp/api/windows.devices.adc.provider)

ProviderAdcChannelMode

### <a name="windowsdevicesbackgroundhttpsdocsmicrosoftcomuwpapiwindowsdevicesbackground"></a>[Windows. デバイス. 背景](https://docs.microsoft.com/uwp/api/windows.devices.background)

DeviceServicingDetails </br> DeviceUseDetails

### <a name="windowsdevicesbluetoothhttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetooth"></a>[Windows. デバイス. Bluetooth](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth)

BluetoothAdapter </br> BluetoothAddressType </br> BluetoothCacheMode </br> BluetoothClassOfDevice </br> BluetoothConnectionStatus </br> BluetoothDevice </br> BluetoothDeviceId </br> BluetoothError </br> BluetoothLEAppearance </br> BluetoothLEAppearanceCategories </br> BluetoothLEAppearanceSubcategories </br> BluetoothLEDevice </br> BluetoothMajorClass </br> BluetoothMinorClass </br> BluetoothServiceCapabilities </br> BluetoothSignalStrengthFilter </br> BluetoothUuidHelper

### <a name="windowsdevicesbluetoothadvertisementhttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetoothadvertisement"></a>[Windows. デバイス. Bluetooth. 提供情報](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth.Advertisement)

BluetoothLEAdvertisement </br> BluetoothLEAdvertisementBytePattern </br> BluetoothLEAdvertisementDataSection </br> BluetoothLEAdvertisementDataTypes </br> BluetoothLEAdvertisementFilter </br> BluetoothLEAdvertisementFlags </br> BluetoothLEAdvertisementPublisher </br> BluetoothLEAdvertisementPublisherStatus </br> BluetoothLEAdvertisementPublisherStatusChangedEventArgs </br> BluetoothLEAdvertisementReceivedEventArgs </br> BluetoothLEAdvertisementType </br> BluetoothLEAdvertisementWatcher </br> BluetoothLEAdvertisementWatcherStatus </br> BluetoothLEAdvertisementWatcherStoppedEventArgs </br> BluetoothLEManufacturerData </br> BluetoothLEScanningMode

### <a name="windowsdevicesbluetoothbackgroundhttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetoothbackground"></a>[Windows. Devices. Background](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth.Background)

BluetoothEventTriggeringMode </br> BluetoothLEAdvertisementPublisherTriggerDetails </br> BluetoothLEAdvertisementWatcherTriggerDetails </br> GattCharacteristicNotificationTriggerDetails </br> G/Serviceproviderconnection </br> G/Serviceprovidertriggerdetails </br> RfcommConnectionTriggerDetails </br> RfcommInboundConnectionInformation </br> RfcommOutboundConnectionInformation

### <a name="windowsdevicesbluetoothgenericattributeprofilehttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetoothgenericattributeprofile"></a>[Windows.Devices.Bluetooth.GenericAttributeProfile](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth.GenericAttributeProfile)

G添付の特性 </br> GattCharacteristicProperties </br> GattCharacteristicUuids </br> GattCharacteristicsResult </br> GattClientCharacteristicConfigurationDescriptorValue </br> G/Clientnotificationresult </br> GattCommunicationStatus </br> G添付記述子 </br> G添付記述子 Uuid </br> G添付記述子 Sresult </br> G添付 Deviceservice </br> GattDeviceServicesResult </br> G/Local特性 </br> GattLocalCharacteristicParameters </br> GattLocalCharacteristicResult </br> G/Localdescriptor </br> Gdependency Local記述子パラメーター </br> G/Local記述子の結果 </br> GattLocalService </br> GattOpenStatus </br> G添付ファイルの形式 </br> G添付プレゼンテーションの Formattypes </br> G/Protectionlevel </br> Gて Protocolerror </br> GattReadClientCharacteristicConfigurationDescriptorResult </br> G添付 Readrequest </br> GattReadRequestedEventArgs </br> Gアタッチ Readresult </br> GattReliableWriteTransaction </br> GattRequestState </br> GattRequestStateChangedEventArgs </br> G添付 Serviceprovider </br> GattServiceProviderAdvertisementStatus </br> GattServiceProviderAdvertisementStatusChangedEventArgs </br> GattServiceProviderAdvertisingParameters </br> G/Serviceproviderresult </br> GattServiceUuids </br> G/Session </br> Gアタッチ Sessionstatus </br> GattSessionStatusChangedEventArgs </br> G/Sharingmode </br> GattSubscribedClient </br> GattValueChangedEventArgs </br> G添付 Writeoption </br> GattWriteRequest </br> GattWriteRequestedEventArgs </br> GattWriteResult

### <a name="windowsdevicesbluetoothrfcommhttpsdocsmicrosoftcomuwpapiwindowsdevicesbluetoothrfcomm"></a>[Windows. Rfcomm](https://docs.microsoft.com/uwp/api/Windows.Devices.Bluetooth.Rfcomm)

RfcommDeviceService </br> RfcommDeviceServicesResult </br> RfcommServiceId </br> RfcommServiceProvider

### <a name="windowsdevicescustomhttpsdocsmicrosoftcomuwpapiwindowsdevicescustom"></a>[Windows. Devices. カスタム](https://docs.microsoft.com/uwp/api/Windows.Devices.Custom)

CustomDevice </br> CustomDeviceContract </br> DeviceAccessMode </br> DeviceSharingMode </br> IOControlCode </br> KnownDeviceTypes

### <a name="windowsdevicesenumerationhttpsdocsmicrosoftcomuwpapiwindowsdevicesenumeration"></a>[Windows.Devices.Enumeration](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration)

DeviceAccessChangedEventArgs </br> DeviceAccessInformation </br> DeviceAccessStatus </br> DeviceClass </br> DeviceConnectionChangeTriggerDetails </br> DeviceDisconnectButtonClickedEventArgs </br> DeviceInformation </br> DeviceInformationCollection </br> DeviceInformationCustomPairing </br> DeviceInformationKind </br> DeviceInformationPairing </br> DeviceInformationUpdate </br> DevicePairingKinds </br> DevicePairingProtectionLevel </br> DevicePairingRequestedEventArgs </br> DevicePairingResult </br> DevicePairingResultStatus </br> DevicePickerDisplayStatusOptions </br> DevicePickerFilter </br> DeviceSelectedEventArgs </br> DeviceThumbnail </br> DeviceUnpairingResult </br> DeviceUnpairingResultStatus </br> DeviceWatcher </br> DeviceWatcherEvent </br> DeviceWatcherEventKind </br> DeviceWatcherStatus </br> DeviceWatcherTriggerDetails </br> EnclosureLocation </br> IDevicePairingSettings </br> Panel

### <a name="windowsdevicesenumerationpnphttpsdocsmicrosoftcomuwpapiwindowsdevicesenumerationpnp"></a>[Windows. デバイス. 列挙型。](https://docs.microsoft.com/uwp/api/Windows.Devices.Enumeration.Pnp)

PnpObject </br> PnpObjectCollection </br> PnpObjectType </br> PnpObjectUpdate </br> PnpObjectWatcher

### <a name="windowsdevicesgpiohttpsdocsmicrosoftcomuwpapiwindowsdevicesgpio"></a>[Windows. デバイス. Gpio](https://docs.microsoft.com/uwp/api/Windows.Devices.Gpio)

GpioChangeCount </br> GpioChangeCounter </br> GpioChangePolarity </br> GpioChangeReader </br> GpioChangeRecord </br> GpioController </br> GpioOpenStatus </br> GpioPin </br> GpioPinDriveMode </br> GpioPinEdge </br> GpioPinValue </br> GpioPinValueChangedEventArgs </br> GpioSharingMode

### <a name="windowsdevicesgpioproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicesgpioprovider"></a>[Windows. デバイス. Gpio. プロバイダー](https://docs.microsoft.com/uwp/api/Windows.Devices.Gpio.Provider)

GpioPinProviderValueChangedEventArgs </br> Igpioコントローラープロバイダー </br> IGpioPinProvider </br> IGpioProvider </br> ProviderGpioPinDriveMode </br> ProviderGpioPinEdge </br> ProviderGpioPinValue </br> ProviderGpioSharingMode

### <a name="windowsdeviceshumaninterfacedevicehttpsdocsmicrosoftcomuwpapiwindowsdeviceshumaninterfacedevice"></a>[HumanInterfaceDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.HumanInterfaceDevice)

HidBooleanControl </br> HidBooleanControlDescription </br> HidCollection </br> HidCollectionType </br> HidDevice </br> HidFeatureReport </br> HidInputReport </br> HidInputReportReceivedEventArgs </br> HidNumericControl </br> HidNumericControlDescription </br> HidOutputReport </br> HidReportType

### <a name="windowsdevicesi2chttpsdocsmicrosoftcomuwpapiwindowsdevicesi2c"></a>[Windows. Devices. I2c](https://docs.microsoft.com/uwp/api/Windows.Devices.I2c)

I2cBusSpeed </br> I2cConnectionSettings </br> I2cController </br> I2cDevice </br> I2cSharingMode </br> I2cTransferResult </br> I2cTransferStatus </br> II2cDeviceStatics

### <a name="windowsdevicesi2cproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicesi2cprovider"></a>[Windows. デバイス. I2c. プロバイダー](https://docs.microsoft.com/uwp/api/Windows.Devices.I2c.Provider)

II2cControllerProvider </br> II2cDeviceProvider </br> II2cProvider </br> ProviderI2cBusSpeed </br> ProviderI2cConnectionSettings </br> ProviderI2cSharingMode </br> ProviderI2cTransferResult </br> ProviderI2cTransferStatus

### <a name="windowsdevicespowerhttpsdocsmicrosoftcomuwpapiwindowsdevicespower"></a>[Windows. Devices. Power](https://docs.microsoft.com/uwp/api/Windows.Devices.Power)

[バッテリー] </br> BatteryReport

### <a name="windowsdevicespwmhttpsdocsmicrosoftcomuwpapiwindowsdevicespwm"></a>[Pwm](https://docs.microsoft.com/uwp/api/Windows.Devices.Pwm)

PwmController </br> PwmPin </br> PwmPulsePolarity

### <a name="windowsdevicespwmproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicespwmprovider"></a>[Windows. Pwm](https://docs.microsoft.com/uwp/api/Windows.Devices.Pwm.Provider)

Ipwmコントローラープロバイダー </br> IPwmProvider

### <a name="windowsdevicesradioshttpsdocsmicrosoftcomuwpapiwindowsdevicesradios"></a>[Windows. デバイス. ラジオ](https://docs.microsoft.com/uwp/api/Windows.Devices.Radios)

83'7b </br> RadioAccessStatus </br> 角丸 Okind </br> RadioState

### <a name="windowsdevicessensorshttpsdocsmicrosoftcomuwpapiwindowsdevicessensors"></a>[Windows.Devices.Sensors](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors)

Accelerometer </br> AccelerometerDataThreshold </br> AccelerometerReading </br> AccelerometerReadingChangedEventArgs </br> AccelerometerReadingType </br> AccelerometerShakenEventArgs </br> ActivitySensor </br> ActivitySensorReading </br> ActivitySensorReadingChangeReport </br> ActivitySensorReadingChangedEventArgs </br> ActivitySensorReadingConfidence </br> ActivitySensorTriggerDetails </br> ActivityType </br> 高度計 </br> AltimeterReading </br> AltimeterReadingChangedEventArgs </br> 気圧計 </br> BarometerDataThreshold </br> BarometerReading </br> BarometerReadingChangedEventArgs </br> Compass </br> CompassDataThreshold </br> CompassReading </br> CompassReadingChangedEventArgs </br> Gyrometer </br> GyrometerDataThreshold </br> GyrometerReading </br> GyrometerReadingChangedEventArgs </br> HingeAngleReading </br> HingeAngleSensor </br> HingeAngleSensorReadingChangedEventArgs </br> ISensorDataThreshold </br>  傾斜計 </br> InclinometerDataThreshold </br> InclinometerReading </br> InclinometerReadingChangedEventArgs </br> LightSensor </br> ライト Sensordatathreshold </br> ライト Sensor読み取り </br> LightSensorReadingChangedEventArgs </br> 磁力計 </br> MagnetometerAccuracy </br> MagnetometerDataThreshold </br> MagnetometerReading </br> MagnetometerReadingChangedEventArgs </br> OrientationSensor </br> OrientationSensorReading </br> OrientationSensorReadingChangedEventArgs </br> 万歩計 </br> PedometerDataThreshold </br> PedometerReading </br> PedometerReadingChangedEventArgs </br> PedometerStepKind </br> ProximitySensor </br> ProximitySensorDataThreshold </br> ProximitySensorDisplayOnOffController </br> ProximitySensorReading </br> ProximitySensorReadingChangedEventArgs </br> SensorDataThresholdTriggerDetails </br> SensorOptimizationGoal </br> SensorQuaternion 数 </br> SensorReadingType </br> SensorRotationMatrix </br> SensorType </br> SimpleOrientation </br> SimpleOrientationSensor </br> SimpleOrientationSensorOrientationChangedEventArgs

### <a name="windowsdevicessensorscustomhttpsdocsmicrosoftcomuwpapiwindowsdevicessensorscustom"></a>[Windows. デバイス... カスタム](https://docs.microsoft.com/uwp/api/Windows.Devices.Sensors.Custom)

CustomSensor </br> CustomSensorReading </br> CustomSensorReadingChangedEventArgs

### <a name="windowsdevicesserialcommunicationhttpsdocsmicrosoftcomuwpapiwindowsdevicesserialcommunication"></a>[SerialCommunication](https://docs.microsoft.com/uwp/api/Windows.Devices.SerialCommunication)

ErrorReceivedEventArgs </br> PinChangedEventArgs </br> SerialDevice </br> SerialError </br> SerialHandshake </br> SerialParity </br> SerialPinChange </br> SerialStopBitCount

### <a name="windowsdevicesspihttpsdocsmicrosoftcomuwpapiwindowsdevicesspi"></a>[Windows. デバイス. Spi](https://docs.microsoft.com/uwp/api/Windows.Devices.Spi)

ISpiDeviceStatics </br> SpiBusInfo </br> SpiConnectionSettings </br> SpiController </br> SpiDevice </br> SpiMode </br> SpiSharingMode

### <a name="windowsdevicesspiproviderhttpsdocsmicrosoftcomuwpapiwindowsdevicesspiprovider"></a>[Windows. デバイス. Spi](https://docs.microsoft.com/uwp/api/Windows.Devices.Spi.Provider)

ISpiControllerProvider </br> ISpiDeviceProvider </br> ISpiProvider </br> ProviderSpiConnectionSettings </br> ProviderSpiMode </br> ProviderSpiSharingMode

### <a name="windowsdevicesusbhttpsdocsmicrosoftcomuwpapiwindowsdevicesusb"></a>[Windows. Devices. Usb](https://docs.microsoft.com/uwp/api/Windows.Devices.Usb)

UsbBulkInEndpointDescriptor </br> UsbBulkInPipe </br> UsbBulkOutEndpointDescriptor </br> UsbBulkOutPipe </br> UsbConfiguration </br> UsbConfigurationDescriptor </br> UsbControlRecipient </br> UsbControlRequestType </br> UsbControlTransferType </br> UsbDescriptor </br> UsbDevice </br> UsbDeviceClass </br> UsbDeviceClasses 場合 </br> UsbDeviceDescriptor </br> UsbEndpointDescriptor </br> UsbEndpointType </br> UsbInterface </br> UsbInterfaceDescriptor </br> UsbInterfaceSetting </br> UsbInterruptInEndpointDescriptor </br> UsbInterruptInEventArgs </br> UsbInterruptInPipe </br> UsbInterruptOutEndpointDescriptor </br> UsbInterruptOutPipe </br> UsbReadOptions </br> UsbSetupPacket </br> UsbTransferDirection </br> UsbWriteOptions

### <a name="windowsdeviceswifihttpsdocsmicrosoftcomuwpapiwindowsdeviceswifi"></a>[Windows. Wi-fi](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi)

WiFiAccessStatus </br> WiFiAdapter </br> WiFiAvailableNetwork </br> WiFiConnectionMethod </br> WiFiConnectionResult </br> WiFiConnectionStatus </br> WiFiNetworkKind </br> WiFiNetworkReport </br> WiFiPhyKind </br> Wi焼討 Connectionkind </br> WiFiWpsConfigurationResult </br> WiFiWpsConfigurationStatus </br> WiFiWpsKind

## <a name="windowsfoundation"></a>Windows.Foundation

### <a name="windowsfoundationhttpsdocsmicrosoftcomuwpapiwindowsfoundation"></a>[Windows.Foundation](https://docs.microsoft.com/uwp/api/Windows.Foundation)

AsyncActionCompletedHandler </br> Asyncaction進行 Shandand氏 </br> AsyncActionWithProgressCompletedHandler </br> AsyncOperationCompletedHandler </br> AsyncOperationProgressHandler </br> AsyncOperationWithProgressCompletedHandler </br> AsyncStatus </br> DateTime </br> 遅延 </br> DeferralCompletedHandler </br> ハンドラー </br> EventRegistrationToken </br> 見つかり Ationcontract </br> GuidHelper </br> HResult </br> IAsyncAction </br> IAsyncActionWithProgress </br> IAsyncInfo </br> IAsyncOperationWithProgress </br> IAsyncOperation </br> Windows.foundation.iclosable </br> IGetActivationFactory </br> IMemoryBuffer </br> IMemoryBufferReference </br> IPropertyValue </br> IReferenceArray </br> IReference </br> IStringable </br> IWwwFormUrlDecoderEntry </br> MemoryBuffer </br> ポイント </br> PropertyType </br> PropertyValue </br> Rect </br> Size </br> TimeSpan </br> Windows.foundation.typedeventhandler<tsender </br> UniversalApiContract </br> URI </br> WwwFormUrlDecoder </br> WwwFormUrlDecoderEntry

### <a name="windowsfoundationcollectionshttpsdocsmicrosoftcomuwpapiwindowsfoundationcollections"></a>[Windows. Foundation. コレクション](https://docs.microsoft.com/uwp/api/Windows.Foundation.Collections)

CollectionChange </br> IIterable </br> Iiterator<t> </br> Ikeyvaluepair<k, </br> 」 </br> IMapView </br> IMap </br> IObservableMap </br> IObservableVector </br> IPropertySet </br> IVectorChangedEventArgs </br> IVectorView </br> IVector </br> MapChangedEventHandler </br> PropertySet </br> StringMap </br> ValueSet </br> VectorChangedEventHandler

### <a name="windowsfoundationdiagnosticshttpsdocsmicrosoftcomuwpapiwindowsfoundationdiagnostics"></a>[Windows. Foundation. 診断](https://docs.microsoft.com/uwp/api/Windows.Foundation.Diagnostics)

AsyncCausalityTracer </br> CausalityRelation </br> CausalitySource </br> CausalitySynchronousWork </br> CausalityTraceLevel </br> ErrorDetails </br> ErrorOptions </br> FileLoggingSession </br> IErrorReportingSettings </br> Ifileログインセッション </br> ILoggingChannel </br> ILoggingSession </br> ILoggingTarget </br> LogFileGeneratedEventArgs </br> ログインアクティビティ </br> LoggingChannel </br> LoggingChannelOptions </br> ログイン Fieldformat </br> ログインフィールド </br> Logginglevel.information </br> ログインオペコード </br> ログインオプション </br> LoggingSession </br> RuntimeBrokerErrorSettings </br> TracingStatusChangedEventArgs

### <a name="windowsfoundationmetadatahttpsdocsmicrosoftcomuwpapiwindowsfoundationmetadata"></a>[Windows. Foundation. メタデータ](https://docs.microsoft.com/uwp/api/Windows.Foundation.Metadata)

ActivatableAttribute </br> AllowForWebAttribute </br> Allow多重属性 </br> ApiContractAttribute </br> ApiInformation </br> AttributeNameAttribute </br> AttributeTargets </br> AttributeUsageAttribute </br> ComposableAttribute </br> CompositionType </br> ContractVersionAttribute </br> CreateFromStringAttribute </br> DefaultAttribute </br> Windows.foundation.metadata.defaultoverloadattribute </br> Windows.foundation.deprecatedattribute </br> DeprecationType </br> DualApiPartitionAttribute </br> ExclusiveToAttribute </br> ExperimentalAttribute </br> FastAbiAttribute </br> FeatureAttribute </br> FeatureStage </br> GCPressureAmount </br> GCPressureAttribute </br> GuidAttribute </br> HasVariantAttribute </br> InternalAttribute </br> LengthIsAttribute </br> ある marshalingbehaviorattribute </br> Marshalingtype.none </br> MetadataMarshalAttribute </br> MuseAttribute </br> NoExceptionAttribute </br> OverloadAttribute </br> OverridableAttribute </br> プラットフォーム </br> PlatformAttribute </br> PreviousContractVersionAttribute </br> ProtectedAttribute </br> RangeAttribute </br> RemoteAsyncAttribute </br> StaticAttribute </br> ThreadingAttribute </br> ThreadingModel </br> VariantAttribute </br> VersionAttribute </br> WebHostHiddenAttribute

### <a name="windowsfoundationnumericshttpsdocsmicrosoftcomuwpapiwindowsfoundationnumerics"></a>[Windows. Foundation. 数値](https://docs.microsoft.com/uwp/api/Windows.Foundation.Numerics)

Matrix3x2 </br> Matrix4x4 </br> 航空 </br> Quaternion </br> 的 </br> Vector2 </br> Vector3 </br> Vector4

## <a name="windowsglobalization"></a>Windows.Globalization

### <a name="windowsglobalizationhttpsdocsmicrosoftcomuwpapiwindowsglobalization"></a>[Windows.Globalization](https://docs.microsoft.com/uwp/api/Windows.Globalization)

ApplicationLanguages </br> カレンダー </br> CalendarIdentifiers </br> ClockIdentifiers </br> CurrencyAmount </br> CurrencyIdentifiers </br> DayOfWeek </br> GeographicRegion </br> 言語 </br> LanguageLayoutDirection </br> NumeralSystemIdentifiers

### <a name="windowsglobalizationcollationhttpsdocsmicrosoftcomuwpapiwindowsglobalizationcollation"></a>[Windows. グローバリゼーション. 照合順序](https://docs.microsoft.com/uwp/api/Windows.Globalization.Collation)

文字のグループ化 </br> 文字のグループ化

### <a name="windowsglobalizationdatetimeformattinghttpsdocsmicrosoftcomuwpapiwindowsglobalizationdatetimeformatting"></a>[Windows.globalization.datetimeformatting](https://docs.microsoft.com/uwp/api/Windows.Globalization.DateTimeFormatting)

DateTimeFormatter </br> DayFormat </br> DayOfWeekFormat </br> 形式 </br> MinuteFormat </br> 月の形式 </br> 同じ形式 </br> YearFormat

### <a name="windowsglobalizationnumberformattinghttpsdocsmicrosoftcomuwpapiwindowsglobalizationnumberformatting"></a>[Windows. グローバリゼーション. 数値書式設定](https://docs.microsoft.com/uwp/api/Windows.Globalization.NumberFormatting)

CurrencyFormatter </br> CurrencyFormatterMode </br> DecimalFormatter </br> INumberFormatter </br> INumberFormatter2 </br> INumberFormatterOptions </br> INumberParser </br> INumberRounder </br> INumberRounderOption </br> Isigned0 オプション </br> ISignificantDigitsOption </br> IncrementNumberRounder </br> NumeralSystemTranslator </br> PercentFormatter </br> Perミル Leformatter </br> RoundingAlgorithm </br> SignificantDigitsNumberRounder

### <a name="windowsglobalizationphonenumberformattinghttpsdocsmicrosoftcomuwpapiwindowsglobalizationphonenumberformatting"></a>[PhoneNumberFormatting](https://docs.microsoft.com/uwp/api/Windows.Globalization.PhoneNumberFormatting)

PhoneNumberFormat </br> PhoneNumberFormatter </br> PhoneNumberInfo </br> PhoneNumberMatchResult </br> PhoneNumberParseResult </br> PredictedPhoneNumberKind

## <a name="windowsgraphics"></a>Windows.Graphics

### <a name="windowsgraphicshttpsdocsmicrosoftcomuwpapiwindowsgraphics"></a>[Windows. Graphics](https://docs.microsoft.com/uwp/api/Windows.Graphics)

DisplayAdapterId

### <a name="windowsgraphicsdirectxhttpsdocsmicrosoftcomuwpapiwindowsgraphicsdirectx"></a>[Windows.Graphics.DirectX](https://docs.microsoft.com/uwp/api/Windows.Graphics.DirectX)

Directxpixel 形式

### <a name="windowsgraphicsdirectxdirect3d11httpsdocsmicrosoftcomuwpapiwindowsgraphicsdirectxdirect3d11"></a>[Windows. Direct3D11](https://docs.microsoft.com/uwp/api/Windows.Graphics.DirectX.Direct3D11)

Direct3DMultisampleDescription </br> Direct3DSurfaceDescription </br> IDirect3DDevice </br> IDirect3DSurface

### <a name="windowsgraphicsdisplayhttpsdocsmicrosoftcomuwpapiwindowsgraphicsdisplay"></a>[Windows. Graphics. Display](https://docs.microsoft.com/uwp/api/Windows.Graphics.Display)

Windows... DisplayOrientations 表示方向

### <a name="windowsgraphicsimaginghttpsdocsmicrosoftcomuwpapiwindowsgraphicsimaging"></a>[Windows.Graphics.Imaging](https://docs.microsoft.com/uwp/api/Windows.Graphics.Imaging)

> [!NOTE]
> この名前空間の一部の Api は、Windows ML コンテナーで使用される場合に制限があります。 詳細については、「[**制限事項**](#limitations)」をご覧ください。

BitmapAlphaMode </br> BitmapBounds </br> BitmapBuffer </br> BitmapBufferAccessMode </br> BitmapCodecInformation </br> BitmapDecoder </br> BitmapEncoder </br> BitmapFlip </br> System.windows.media.imaging.bitmapframe> </br> BitmapInterpolationMode </br> BitmapPixelFormat </br> BitmapPlaneDescription </br> BitmapProperties </br> BitmapPropertiesView </br> BitmapPropertySet </br> BitmapRotation </br> BitmapSize </br> BitmapTransform </br> BitmapTypedValue </br> ColorManagementMode </br> ExifOrientationMode </br> IBitmapFrame </br> Ibitmapフレーム Withソフトウェアビットマップ </br> IBitmapPropertiesView </br> ImageStream </br> JpegSubsamplingMode </br> ピクセル Dataprovider </br> PngFilterMode </br> SoftwareBitmap </br> TiffCompressionMode

## <a name="windowsmedia"></a>Windows.Media

### <a name="windowsmediahttpsdocsmicrosoftcomuwpapiwindowsmedia"></a>[Windows. メディア](https://docs.microsoft.com/uwp/api/Windows.Media)

AudioBuffer </br> AudioBufferAccessMode </br> AudioFrame </br> AudioProcessing </br> AutoRepeatModeChangeRequestedEventArgs </br> IMediaExtension </br> IMediaFrame </br> IMediaMarker </br> IMediaMarkers </br> ImageDisplayProperties </br> MediaMarkerTypes </br> MediaPlaybackAutoRepeatMode </br> MediaPlaybackStatus </br> MediaPlaybackType </br> MediaProcessingTriggerDetails </br> メディア </br> MediaTimelineController </br> MediaTimelineControllerFailedEventArgs </br> MediaTimelineControllerState </br> MusicDisplayProperties </br> PlaybackPositionChangeRequestedEventArgs </br> PlaybackRateChangeRequestedEventArgs </br> ShuffleEnabledChangeRequestedEventArgs </br> SoundLevel </br> SystemMediaTransportControls </br> SystemMediaTransportControlsButton </br> SystemMediaTransportControlsButtonPressedEventArgs </br> SystemMediaTransportControlsDisplayUpdater </br> SystemMediaTransportControlsProperty </br> SystemMediaTransportControlsPropertyChangedEventArgs </br> SystemMediaTransportControlsTimelineProperties </br> VideoDisplayProperties </br> VideoEffects </br> VideoFrame

## <a name="windowsnetworking"></a>Windows.Networking

### <a name="windowsnetworkinghttpsdocsmicrosoftcomuwpapiwindowsnetworking"></a>[Windows. ネットワーク](https://docs.microsoft.com/uwp/api/Windows.Networking)

DomainNameType </br> EndpointPair </br> ホスト名 </br> HostNameSortOptions </br> HostNameType 場合

### <a name="windowsnetworkingbackgroundtransferhttpsdocsmicrosoftcomuwpapiwindowsnetworkingbackgroundtransfer"></a>[Windows. ネットワーク. BackgroundTransfer](https://docs.microsoft.com/uwp/api/Windows.Networking.BackgroundTransfer)

BackgroundDownloadProgress </br> BackgroundTransferBehavior </br> Backgroundtransfer○グループ </br> Backgroundtransfer補完 Grouptriggerdetails </br> BackgroundTransferContentPart </br> Backgroundtransferコストポリシー </br> BackgroundTransferError </br> BackgroundTransferFileRange </br> BackgroundTransferGroup </br> BackgroundTransferPriority </br> BackgroundTransferRangesDownloadedEventArgs </br> BackgroundTransferStatus </br> BackgroundUploadProgress </br> ContentPrefetcher </br> DownloadOperation </br> IBackgroundTransferBase </br> IBackgroundTransferContentPartFactory </br> IBackgroundTransferOperation </br> IBackgroundTransferOperationPriority </br> ResponseInformation </br> UnconstrainedTransferRequestResult </br> UploadOperation

### <a name="windowsnetworkingconnectivityhttpsdocsmicrosoftcomuwpapiwindowsnetworkingconnectivity"></a>[Windows.Networking.Connectivity](https://docs.microsoft.com/uwp/api/Windows.Networking.Connectivity)

AttributedNetworkUsage </br> CellularApnAuthenticationType </br> CellularApnContext </br> ConnectionCost </br> ConnectionProfile </br> ConnectionProfileDeleteStatus </br> ConnectionProfileFilter </br> ConnectionSession </br> ConnectivityInterval </br> ConnectivityManager </br> Dataplan の状態 </br> Dataplan の使用 </br> DataUsage </br> Dataて粒度 </br> DomainConnectivityLevel </br> LanIdentifier </br> LanIdentifierData </br> NetworkAdapter </br> NetworkAuthenticationType </br> NetworkConnectivityLevel </br> NetworkCostType </br> NetworkEncryptionType </br> System.net.networkinformation </br> NetworkItem </br> NetworkSecuritySettings </br> NetworkStateChangeEventDetails </br> NetworkStatusChangedEventHandler </br> NetworkTypes </br> NetworkUsage </br> NetworkUsageStates </br> ProviderNetworkUsage </br> ProxyConfiguration </br> RoamingStates </br> RoutePolicy </br> TriStates </br> WlanConnectionProfileDetails </br> WwanConnectionProfileDetails </br> WwanContract </br> WwanDataClass </br> WwanNetworkIPKind </br> WwanNetworkRegistrationState

### <a name="windowsnetworkingsocketshttpsdocsmicrosoftcomuwpapiwindowsnetworkingsockets"></a>[Windows.Networking.Sockets](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets)

BandwidthStatistics </br> ControlChannelTrigger </br> ControlChannelTriggerContract </br> ControlChannelTriggerResetReason </br> ControlChannelTriggerResourceType </br> ControlChannelTriggerStatus </br> DatagramSocket </br> DatagramSocketControl </br> DatagramSocketInformation </br> DatagramSocketMessageReceivedEventArgs </br> IControlChannelTriggerEventDetails </br> IControlChannelTriggerResetEventDetails </br> IWebSocket </br> IWebSocketControl </br> IWebSocketControl2 </br> IWebSocketInformation </br> IWebSocketInformation2 </br> MessageWebSocket </br> MessageWebSocketControl </br> MessageWebSocketInformation </br> MessageWebSocketMessageReceivedEventArgs </br> MessageWebSocketReceiveMode </br> RoundTripTimeStatistics </br> ServerMessageWebSocket </br> ServerMessageWebSocketControl </br> ServerMessageWebSocketInformation </br> ServerStreamWebSocket </br> ServerStreamWebSocketInformation </br> Socketactivityconnectedスタンド Byaction </br> SocketActivityContext </br> SocketActivityInformation </br> SocketActivityKind </br> SocketActivityTriggerDetails </br> SocketActivityTriggerReason </br> SocketError </br> SocketErrorStatus </br> SocketMessageType </br> SocketProtectionLevel </br> SocketQualityOfService </br> SocketSslErrorSeverity </br> StreamSocket </br> StreamSocketControl </br> StreamSocketInformation </br> StreamSocketListener </br> StreamSocketListenerConnectionReceivedEventArgs </br> StreamSocketListenerControl </br> StreamSocketListenerInformation </br> StreamWebSocket </br> StreamWebSocketControl </br> StreamWebSocketInformation </br> WebSocketClosedEventArgs </br> WebSocketError </br> WebSocketServerCustomValidationRequestedEventArgs

## <a name="windowssecurity"></a>Windows. セキュリティ

### <a name="windowssecuritycredentialshttpsdocsmicrosoftcomuwpapiwindowssecuritycredentials"></a>[Windows. Security. 資格情報](https://docs.microsoft.com/uwp/api/Windows.Security.Credentials)

PasswordCredential

### <a name="windowssecuritycryptographyhttpsdocsmicrosoftcomuwpapiwindowssecuritycryptography"></a>[Windows. Security. Cryptography](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography)

BinaryStringEncoding </br> CryptographicBuffer

### <a name="windowssecuritycryptographycertificateshttpsdocsmicrosoftcomuwpapiwindowssecuritycryptographycertificates"></a>[Windows. Security. Cryptography. 証明書](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography.Certificates)

Certificate </br> 一対一 </br> ポリシーのポリシー </br> CertificateEnrollmentManager </br> CertificateExtension </br> CertificateKeyUsages </br> CertificateQuery </br> 「Windows.security.cryptography.certificates.certificaterequestproperties </br> CertificateStore </br> CertificateStores </br> ChainBuildingParameters </br> ChainValidationParameters </br> ChainValidationResult </br> CmsAttachedSignature </br> CmsDetachedSignature </br> CmsSignerInfo </br> CmsTimestampInfo </br> EnrollKeyUsages </br> ExportOption </br> InstallOptions </br> KeyAlgorithmNames </br> KeyAttestationHelper </br> KeyProtectionLevel </br> KeySize </br> KeyStorageProviderNames </br> PfxImportParameters </br> SignatureValidationResult </br> StandardCertificateStoreNames エイリアス </br> Subject代替情報 </br> UserCertificateEnrollmentManager </br> UserCertificateStore

### <a name="windowssecuritycryptographycorehttpsdocsmicrosoftcomuwpapiwindowssecuritycryptographycore"></a>[Windows. Security. Cryptography. Core](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography.Core)

AsymmetricAlgorithmNames </br> AsymmetricKeyAlgorithmProvider </br> Capi1KdfTargetAlgorithm </br> CryptographicEngine </br> CryptographicHash </br> CryptographicKey </br> CryptographicPadding </br> CryptographicPrivateKeyBlobType </br> CryptographicPublicKeyBlobType </br> EccCurveNames </br> Encryptedand認証 Ateddata </br> HashAlgorithmNames </br> HashAlgorithmProvider </br> KeyDerivationAlgorithmNames </br> KeyDerivationAlgorithmProvider </br> KeyDerivationParameters </br> MacAlgorithmNames </br> MacAlgorithmProvider </br> PersistedKeyProvider </br> SymmetricAlgorithmNames </br> SymmetricKeyAlgorithmProvider

### <a name="windowssecuritycryptographydataprotectionhttpsdocsmicrosoftcomuwpapiwindowssecuritycryptographydataprotection"></a>[Windows. Cryptography. DataProtection](https://docs.microsoft.com/uwp/api/Windows.Security.Cryptography.DataProtection)

DataProtectionProvider

### <a name="windowssecurityenterprisedatahttpsdocsmicrosoftcomuwpapiwindowssecurityenterprisedata"></a>[Windows. Security. EnterpriseData](https://docs.microsoft.com/uwp/api/Windows.Security.EnterpriseData)

BufferProtectUnprotectResult </br> DataProtectionInfo </br> DataProtectionManager </br> DataProtectionStatus </br> EnforcementLevel </br> EnterpriseDataContract </br> FileProtectionInfo </br> FileProtectionManager </br> FileProtectionStatus </br> FileRevocationManager </br> FileUnprotectOptions </br> ProtectedAccessResumedEventArgs </br> ProtectedAccessSuspendingEventArgs </br> ProtectedContainerExportResult </br> ProtectedContainerImportResult </br> ProtectedContentRevokedEventArgs </br> ProtectedFileCreateResult </br> ProtectedImportExportStatus </br> ProtectionPolicyAuditAction </br> ProtectionPolicyAuditInfo </br> ProtectionPolicyEvaluationResult </br> ProtectionPolicyManager </br> ProtectionPolicyRequestAccessBehavior </br> ThreadNetworkContext

### <a name="windowssecurityexchangeactivesyncprovisioninghttpsdocsmicrosoftcomuwpapiwindowssecurityexchangeactivesyncprovisioning"></a>[Windows.security.exchangeactivesyncprovisioning](https://docs.microsoft.com/uwp/api/Windows.Security.ExchangeActiveSyncProvisioning)

EasClientDeviceInformation </br> EasClientSecurityPolicy </br> EasComplianceResults </br> EasContract </br> EasDisallowConvenienceLogonResult </br> EasEncryptionProviderType </br> EasMaxInactivityTimeLockResult </br> EasMaxPasswordFailedAttemptsResult </br> Easminpasswordcomplexの結果 </br> Easminpasswordlength の結果 </br> EasPasswordExpirationResult </br> Easpasswordhistory の結果 </br> EasRequireEncryptionResult

## <a name="windowsstorage"></a>Windows.Storage

### <a name="windowsstoragehttpsdocsmicrosoftcomuwpapiwindowsstorage"></a>[Windows. ストレージ](https://docs.microsoft.com/uwp/api/Windows.Storage)

AppDataPaths </br> ApplicationData </br> ApplicationDataCompositeValue </br> ApplicationDataContainer </br> ApplicationDataContainerSettings </br> ApplicationDataCreateDisposition </br> ApplicationDataLocality </br> ApplicationDataSetVersionHandler </br> CachedFileManager </br> CreationCollisionOption </br> DownloadsFolder </br> FileAccessMode </br> FileAttributes </br> FileIO </br> IStorageFile </br> IStorageFile2 </br> IStorageFilePropertiesWithAvailability </br> IStorageFolder </br> IStorageFolder2 </br> IStorageItem </br> IStorageItem2 </br> IStorageItemProperties </br> IStorageItemProperties2 </br> IStorageItemPropertiesWithProvider </br> IStreamedFileDataRequest </br> KnownFolderId </br> Knownfolders.h </br> Knownの Accessstatus </br> KnownLibraryId </br> Namecolliのオプション </br> PathIO </br> SetVersionDeferral </br> SetVersionRequest </br> StorageDeleteOption </br> StorageFile </br> StorageFolder </br> StorageItemTypes </br> StorageLibrary </br> StorageLibraryChange </br> StorageLibraryChangeReader </br> StorageLibraryChangeTracker </br> StorageLibraryChangeType </br> StorageOpenOptions </br> StorageProvider </br> StorageStreamTransaction </br> StreamedFileDataRequest </br> StreamedFileDataRequestedHandler </br> StreamedFileFailureMode </br> SystemAudioProperties </br> SystemDataPaths </br> SystemGPSProperties </br> SystemImageProperties </br> SystemMediaProperties </br> SystemMusicProperties </br> SystemPhotoProperties </br> SystemProperties </br> SystemVideoProperties </br> UserDataPaths

### <a name="windowsstorageaccesscachehttpsdocsmicrosoftcomuwpapiwindowsstorageaccesscache"></a>[Windows.Storage.AccessCache](https://docs.microsoft.com/uwp/api/Windows.Storage.AccessCache)

AccessCacheOptions </br> AccessListEntry </br> AccessListEntryView </br> IStorageItemAccessList </br> ItemRemovedEventArgs </br> RecentStorageItemVisibility </br> StorageApplicationPermissions </br> StorageItemAccessList </br> StorageItemMostRecentlyUsedList

### <a name="windowsstoragebulkaccesshttpsdocsmicrosoftcomuwpapiwindowsstoragebulkaccess"></a>[Windows. ストレージの BulkAccess](https://docs.microsoft.com/uwp/api/Windows.Storage.BulkAccess)

FileInformation </br> FileInformationFactory </br> FolderInformation </br> IStorageItemInformation

### <a name="windowsstoragecompressionhttpsdocsmicrosoftcomuwpapiwindowsstoragecompression"></a>[Windows. ストレージ. 圧縮](https://docs.microsoft.com/uwp/api/Windows.Storage.Compression)

CompressAlgorithm </br> コンプレッサー </br> 圧縮

### <a name="windowsstoragefilepropertieshttpsdocsmicrosoftcomuwpapiwindowsstoragefileproperties"></a>[Windows.storage.fileproperties](https://docs.microsoft.com/uwp/api/Windows.Storage.FileProperties)

BasicProperties </br> DocumentProperties </br> IStorageItemExtraProperties </br> ImageProperties </br> MusicProperties </br> PhotoOrientation </br> PropertyPrefetchOptions </br> StorageItemContentProperties </br> StorageItemThumbnail ネイル </br> ThumbnailMode </br> ThumbnailOptions </br> ThumbnailType </br> ビデオの向き </br> VideoProperties

### <a name="windowsstorageproviderhttpsdocsmicrosoftcomuwpapiwindowsstorageprovider"></a>[Windows.Storage.Provider](https://docs.microsoft.com/uwp/api/Windows.Storage.Provider)

CachedFileOptions </br> CachedFileTarget </br> CachedFileUpdater </br> CachedFileUpdaterUI </br> CloudFilesContract </br> Filetable </br> FileUpdateRequestDeferral </br> FileUpdateRequestedEventArgs </br> FileUpdateStatus </br>  IStorageProviderItemPropertySource </br> IStorageProviderPropertyCapabilities </br> IStorageProviderUriSource </br> ReadActivationMode </br> StorageProviderFileTypeInfo </br> StorageProviderGetContentInfoForPathResult </br> StorageProviderGetPathForContentUriResult </br> Storageproviderハードリンクポリシー </br> StorageProviderHydrationPolicy </br> StorageProviderHydrationPolicyModifier </br> StorageProviderInSyncPolicy </br> StorageProviderItemProperties </br> StorageProviderItemProperty </br> StorageProviderItemPropertyDefinition </br> StorageProviderPopulationPolicy </br> StorageProviderProtectionMode </br> StorageProviderSyncRootInfo </br> StorageProviderSyncRootManager </br> StorageProviderUriSourceStatus </br> UIStatus </br> WriteActivationMode

### <a name="windowsstoragesearchhttpsdocsmicrosoftcomuwpapiwindowsstoragesearch"></a>[Windows. Storage. 検索](https://docs.microsoft.com/uwp/api/Windows.Storage.Search)

CommonFileQuery </br> CommonFolderQuery </br> ContentIndexer </br> ContentIndexerQuery </br> DateStackOption </br> FolderDepth </br> IIndexableContent 場合 </br> IStorageFolderQueryOperations </br> IStorageQueryResultBase </br> IndexableContent 場合 </br> IndexedState </br> IndexerOption </br> QueryOptions </br> SortEntry </br> SortEntryVector </br> StorageFileQueryResult </br> StorageFolderQueryResult </br> StorageItemQueryResult </br> StorageLibraryChangeTrackerTriggerDetails </br> Storagelibrarycontentの項目の詳細 </br> ValueAndLanguage

### <a name="windowsstoragestreamshttpsdocsmicrosoftcomuwpapiwindowsstoragestreams"></a>[Windows.Storage.Streams](https://docs.microsoft.com/uwp/api/Windows.Storage.Streams)

バッファー </br> ByteOrder </br> DataReader </br> DataReaderLoadOperation </br> DataWriter </br> DataWriterStoreOperation </br> FileInputStream </br> FileOpenDisposition ポジション </br> FileOutputStream </br> FileRandomAccessStream </br> IBuffer </br>  IContentTypeProvider </br> IDataReader </br> IInputStream </br> IInputStreamReference </br> IOutputStream </br> IRandomAccessStream </br> IRandomAccessStreamReference </br> IRandomAccessStreamWithContentType </br> InMemoryRandomAccessStream </br> InputStreamOptions </br> InputStreamOverStream </br> OutputStreamOverStream </br> Windows.storage.streams.randomaccessstream </br> RandomAccessStreamOverStream </br> RandomAccessStreamReference </br> UnicodeEncoding

## <a name="windowssystem"></a>Windows.System

### <a name="windowssystemhttpsdocsmicrosoftcomuwpapiwindowssystem"></a>[Windows.System](https://docs.microsoft.com/uwp/api/Windows.System)

AppDiagnosticInfoWatcherStatus </br> AppExecutionStateChangeResult </br> AppMemoryReport </br> AppMemoryUsageLevel </br> Appmemoryon Limitの制限 Eventargs </br> AppResourceGroupBackgroundTaskReport </br> AppResourceGroupEnergyQuotaState </br> AppResourceGroupExecutionState </br> AppResourceGroupInfoWatcherStatus </br> AppResourceGroupMemoryReport </br> AppResourceGroupStateReport </br> AppUriHandlerHost </br> AppUriHandlerRegistration </br> AppUriHandlerRegistrationManager </br> AutoUpdateTimeZoneStatus </br> DateTimeSettings </br> DiagnosticAccessStatus </br> DispatcherQueue </br> DispatcherQueueController </br> DispatcherQueueHandler </br> DispatcherQueuePriority </br> DispatcherQueueShutdownStartingEventArgs </br> DispatcherQueueTimer </br> KnownUserProperties </br> LaunchFileStatus </br> LaunchQuerySupportStatus </br> LaunchQuerySupportType </br> LaunchUriResult </br> LaunchUriStatus </br> MemoryManager </br> PowerState </br> ProcessLauncher </br> ProcessLauncherOptions </br> ProcessLauncherResult </br> ProcessMemoryReport </br> ProcessorArchitecture </br> ProtocolForResultsOperation </br> RemoteLaunchUriStatus </br> RemoteLauncherOptions </br> ShutdownKind </br> ShutdownManager </br> SystemManagementContract </br> TimeZoneSettings

### <a name="windowssystemdiagnosticshttpsdocsmicrosoftcomuwpapiwindowssystemdiagnostics"></a>[Windows. Diagnostics](https://docs.microsoft.com/uwp/api/Windows.System.Diagnostics)

DiagnosticActionResult </br> DiagnosticActionState </br> DiagnosticInvoker </br> ProcessCpuUsage </br> ProcessCpuUsageReport </br> ProcessDiskUsage </br> ProcessDiskUsageReport </br> ProcessMemoryUsage </br> ProcessMemoryUsageReport </br> SystemCpuUsage </br> SystemCpuUsageReport </br> SystemDiagnosticInfo </br> SystemMemoryUsage </br> SystemMemoryUsageReport

### <a name="windowssystemdiagnosticstelemetryhttpsdocsmicrosoftcomuwpapiwindowssystemdiagnosticstelemetry"></a>[Windows. Diagnostics. テレメトリ](https://docs.microsoft.com/uwp/api/Windows.System.Diagnostics.Telemetry)

PlatformTelemetryClient </br> PlatformTelemetryRegistrationResult </br> PlatformTelemetryRegistrationSettings </br> PlatformTelemetryRegistrationStatus

### <a name="windowssystemdiagnosticstracereportinghttpsdocsmicrosoftcomuwpapiwindowssystemdiagnosticstracereporting"></a>[Windows...。](https://docs.microsoft.com/uwp/api/Windows.System.Diagnostics.TraceReporting)

PlatformDiagnosticActionState </br> PlatformDiagnosticActions </br> PlatformDiagnosticEscalationType </br> PlatformDiagnosticEventBufferLatencies </br> PlatformDiagnosticTraceInfo </br> PlatformDiagnosticTracePriority </br> PlatformDiagnosticTraceRuntimeInfo </br> PlatformDiagnosticTraceSlotState </br> PlatformDiagnosticTraceSlotType

### <a name="windowssystemdisplayhttpsdocsmicrosoftcomuwpapiwindowssystemdisplay"></a>[Windows. system.string](https://docs.microsoft.com/uwp/api/Windows.System.Display)

DisplayRequest

### <a name="windowssysteminventoryhttpsdocsmicrosoftcomuwpapiwindowssysteminventory"></a>[Windows. System. Inventory](https://docs.microsoft.com/uwp/api/Windows.System.Inventory)

すべてのアプリ

### <a name="windowssystempowerhttpsdocsmicrosoftcomuwpapiwindowssystempower"></a>[Windows. system.string](https://docs.microsoft.com/uwp/api/Windows.System.Power)

BackgroundEnergyManager </br> BatteryStatus </br> EnergySaverStatus </br> ForegroundEnergyManager </br> PowerManager </br> PowerSupplyStatus

### <a name="windowssystempowerdiagnosticshttpsdocsmicrosoftcomuwpapiwindowssystempowerdiagnostics"></a>[Windows... 診断](https://docs.microsoft.com/uwp/api/Windows.System.Power.Diagnostics)

BackgroundEnergyDiagnostics </br> ForegroundEnergyDiagnostics

### <a name="windowssystemprofilehttpsdocsmicrosoftcomuwpapiwindowssystemprofile"></a>[Windows.System.Profile](https://docs.microsoft.com/uwp/api/Windows.System.Profile)

AnalyticsInfo </br> AnalyticsVersionInfo </br> AppApplicability </br> EducationSettings </br> ハードウェア Id </br> ハードウェアトークン </br> KnownRetailInfoProperties </br> PlatformDataCollectionLevel </br> PlatformDiagnosticsAndUsageDataSettings </br> Profileの Tokencontract </br> ProfileRetailInfoContract </br> ProfileSharedModeContract </br> RetailInfo </br> SharedModeSettings </br> SystemIdentification </br> SystemIdentificationInfo </br> SystemIdentificationSource </br> SystemOutOfBoxExperienceState </br> SystemSetupInfo </br> UnsupportedAppRequirement </br> UnsupportedAppRequirementReasons </br> WindowsIntegrityPolicy

### <a name="windowssystemprofilesystemmanufacturershttpsdocsmicrosoftcomuwpapiwindowssystemprofilesystemmanufacturers"></a>[Windows.System.Profile.SystemManufacturers](https://docs.microsoft.com/uwp/api/Windows.System.Profile.SystemManufacturers)

OemSupportInfo </br> SmbiosInformation </br> SystemManufacturersContract </br> SystemSupportDeviceInfo </br> SystemSupportInfo

### <a name="windowssystemthreadinghttpsdocsmicrosoftcomuwpapiwindowssystemthreading"></a>[Windows. system.object](https://docs.microsoft.com/uwp/api/Windows.System.Threading)

ThreadPool </br> ThreadPoolTimer </br> TimerDestroyedHandler </br> TimerElapsedHandler </br> WorkItemHandler </br> WorkItemOptions </br> WorkItemPriority

### <a name="windowssystemthreadingcorehttpsdocsmicrosoftcomuwpapiwindowssystemthreadingcore"></a>[Windows. system.object. コア](https://docs.microsoft.com/uwp/api/Windows.System.Threading.Core)

PreallocatedWorkItem </br> SignalHandler </br> SignalNotifier

### <a name="windowssystemuserhttpsdocsmicrosoftcomuwpapiwindowssystemuser"></a>[Windows. system.string](https://docs.microsoft.com/uwp/api/Windows.System.User)

ユーザー </br> UserAuthenticationStatus </br> UserAuthenticationStatusChangeDeferral </br> Userauthenticationstatus/Eventargs </br> UserChangedEventArgs </br> UserDeviceAssociation </br> UserDeviceAssociationChangedEventArgs </br> UserPicker </br> UserPictureSize </br> UserType </br> UserWatcher </br> UserWatcherStatus </br> UserWatcherUpdateKind </br> VirtualKey </br> VirtualKeyModifiers

## <a name="windowsui"></a>Windows.UI

### <a name="windowsuitextcorehttpsdocsmicrosoftcomuwpapiwindowsuitextcore"></a>[Windows.UI.Text.Core](https://docs.microsoft.com/uwp/api/Windows.UI.Text.Core)

CoreTextInputScope

## <a name="windowsweb"></a>Windows.Web

### <a name="windowswebhttpsdocsmicrosoftcomuwpapiwindowsweb"></a>[Windows. Web](https://docs.microsoft.com/uwp/api/Windows.Web)

IUriToStreamResolver </br> WebError </br> WebErrorStatus

### <a name="windowswebatompubhttpsdocsmicrosoftcomuwpapiwindowswebatompub"></a>[AtomPub](https://docs.microsoft.com/uwp/api/Windows.Web.AtomPub)

AtomPubClient </br> ResourceCollection </br> ServiceDocument </br> ワークスペース

### <a name="windowswebhttphttpsdocsmicrosoftcomuwpapiwindowswebhttp"></a>[Windows.Web.Http](https://docs.microsoft.com/uwp/api/Windows.Web.Http)

HttpBufferContent </br> HttpClient </br> Http[オプション] </br> HttpCookie </br> HttpCookieCollection </br> HttpCookieManager </br> HttpFormUrlEncodedContent </br> HttpGetBufferResult </br> HttpGetInputStreamResult </br> HttpGetStringResult </br> HttpMethod </br> HttpMultipartContent </br> HttpMultipartFormDataContent </br> HttpProgress </br> Http進捗段階 </br> HttpRequestMessage </br> HttpRequestResult </br> HttpResponseMessage </br> HttpResponseMessageSource </br> HttpStatusCode </br> HttpStreamContent </br> HttpStringContent </br> HttpTransportInformation </br> HttpVersion </br> IHttpContent

### <a name="windowswebhttpdiagnosticshttpsdocsmicrosoftcomuwpapiwindowswebhttpdiagnostics"></a>[Windows. Web.config](https://docs.microsoft.com/uwp/api/Windows.Web.Http.Diagnostics)

HttpDiagnosticProvider </br> HttpDiagnosticProviderRequestResponseCompletedEventArgs </br> HttpDiagnosticProviderRequestResponseTimestamps </br> HttpDiagnosticProviderRequestSentEventArgs </br> HttpDiagnosticProviderResponseReceivedEventArgs </br> HttpDiagnosticRequestInitiator </br> HttpDiagnosticSourceLocation </br> HttpDiagnosticsContract

### <a name="windowswebhttpfiltershttpsdocsmicrosoftcomuwpapiwindowswebhttpfilters"></a>[Windows.Web.Http.Filters](https://docs.microsoft.com/uwp/api/Windows.Web.Http.Filters)

HttpBaseProtocolFilter </br> HttpCacheControl </br> HttpCacheReadBehavior </br> HttpCacheWriteBehavior </br> Httpcookieの動作の動作 </br> HttpServerCustomValidationRequestedEventArgs </br> IHttpFilter

### <a name="windowswebhttpheadershttpsdocsmicrosoftcomuwpapiwindowswebhttpheaders"></a>[Windows... ヘッダー](https://docs.microsoft.com/uwp/api/Windows.Web.Http.Headers)

HttpCacheDirectiveHeaderValueCollection </br> HttpChallengeHeaderValue </br> HttpChallengeHeaderValueCollection </br> HttpConnectionOptionHeaderValue </br> HttpConnectionOptionHeaderValueCollection </br> Httpcontentco/Headervalue </br> Httpcontentco/Headervaluecollection </br> HttpContentCodingWithQualityHeaderValue </br> HttpContentCodingWithQualityHeaderValueCollection </br> HttpContentDispositionHeaderValue </br> HttpContentHeaderCollection </br> Httpコンテ Entrangeheadervalue </br> HttpCookiePairHeaderValue </br> HttpCookiePairHeaderValueCollection </br> HttpCredentialsHeaderValue </br> HttpDateOrDeltaHeaderValue </br> HttpExpectationHeaderValue </br> HttpExpectationHeaderValueCollection </br> HttpLanguageHeaderValueCollection </br> HttpLanguageRangeWithQualityHeaderValue </br> HttpLanguageRangeWithQualityHeaderValueCollection </br> HttpMediaTypeHeaderValue </br> HttpMediaTypeWithQualityHeaderValue </br> HttpMediaTypeWithQualityHeaderValueCollection </br> HttpMethodHeaderValueCollection </br> HttpNameValueHeaderValue </br> HttpProductHeaderValue </br> HttpProductInfoHeaderValue </br> HttpProductInfoHeaderValueCollection </br> HttpRequestHeaderCollection </br> HttpResponseHeaderCollection </br> Httptransferco/Headervalue </br> Httptransferco/Headervaluecollection

### <a name="windowswebsyndicationhttpsdocsmicrosoftcomuwpapiwindowswebsyndication"></a>[Windows. Web. 配信](https://docs.microsoft.com/uwp/api/Windows.Web.Syndication)

ISyndicationClient </br> ISyndicationNode </br> ISyndicationText </br> RetrievalProgress </br> SyndicationAttribute </br> SyndicationCategory </br> SyndicationClient </br> SyndicationContent </br> SyndicationError </br> SyndicationErrorStatus </br> SyndicationFeed </br> SyndicationFormat </br> SyndicationGenerator </br> SyndicationItem </br> SyndicationLink </br> SyndicationNode </br> SyndicationPerson </br> SyndicationText </br> SyndicationTextType </br> TransferProgress

## <a name="limitations"></a>制限事項

### <a name="windowsgraphicsimaging"></a>Windows. Graphics. イメージング

Windows ML コンテナーで使用する[場合、いくつかの api](https://docs.microsoft.com/uwp/api/windows.graphics.imaging)には制限があります。 これらの制限は次のとおりです。

* Windows. Graphics. Imaging は、JPG、PNG、GIF、TIFF、および BMP ファイル形式に対してのみエンコードとデコードをサポートします。
* BI_BITFIELDS 圧縮で BMP 形式を使用する場合は、16bppBGR555、16Bppbgr555、および32bppBGRA の形式のみがサポートされます。
* CMYK、高ダイナミックレンジ、ハーフ浮動小数点ピクセル形式、固定ポイントピクセル形式、または4チャネルを超えるイメージはサポートされていません。
* 32bppRGBE、16bppYQuantizedDctCoefficients、16bppCbQuantizedDctCoefficients、および16bppCrQuantizedDctCoefficients ピクセル形式はサポートされていません。
* XMP メタデータまたは[フォトメタデータポリシー](https://docs.microsoft.com/windows/win32/wic/photo-metadata-policies)の読み取りまたは書き込みはサポートされていません。 変換では、可能であれば API が XMP メタデータを保持しようとします。
* Colorspace の操作とメッセージ交換はサポートされていません。
* [Getpixeldataasync](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapdecoder.getpixeldataasync)と[get$ bitmapasync](https://docs.microsoft.com/uwp/api/windows.graphics.imaging.bitmapframe.getsoftwarebitmapasync)には `ColorManageToSRgb` フラグが*部分的*にサポートされています。 フラグが指定されている場合、イメージに一般的に認識されている sRGB カラープロファイルがあると、操作は成功します。 それ以外の場合は、`ERROR_ICM_NOT_ENABLED` に相当する HRESULT が返されます。
