# uhf_plugin

A flutter plugin for UHF type C66 to read UHF Cards. This was forked from the C72 plugin created by amorenew.

I included the newer API version from Chainway and updated for the latest version of Flutter (Oct 2022).

#### Library Pub link

https://pub.dev/packages/uhf_plugin

### Getting Started

- Import the library (NOT public yet):

  `import 'package:uhf_c72_plugin/uhf_c72_plugin.dart';`

- Open connection to the UHF reader

  `await UhfPlugin.connect`

- Check if is the reader connected

  `await UhfPlugin.isConnected;`

- Start reading data a single UHF card

  `await UhfPlugin.startSingle;`

- Start reading data multi 'continuous' UHF cards

  `await UhfPlugin.startContinuous;`

- Is started reading

  `await UhfPlugin.isStarted;`

- Stop Reading

  `await UhfPlugin.stop;`

- Close the connection

  `await UhfPlugin.close;`

- Clear cached data for the reader

  `await UhfPlugin.clearData;`

- Is Empty Tags

  `await UhfPlugin.isEmptyTags;`

- Write to EPC Tag

  `await UhfPlugin.writeEPC(String writeData, String accessPwd)`

- Set Power level (1 dBm : 30 dBm use string numbers)

  `await UhfPlugin.setPowerLevel(String level);`

- Get Power level (returns string number, 1-30 dBm)

  `await UhfPlugin.getPowerLevel;`

- Set Work area (string number)

  - 1：China Standard(840~845MHz)
  - 2：China Standard2(920~925MHz)
  - 4：Europe Standard(865~868MHz)
  - 8：USA(902-928MHz)
  - 22：Korea(917~923MHz)
  - 50: Japan(952~953MHz)
  - 51: South Africa(915~919MHz)
  - 52: China Taiwan
  - 53: Vietnam(918~923MHz)
  - 54: Peru(915MHz-928MHz)
  - 55: Russia( 860MHz-867.6MHz)
  - 128: Morocco

  `await UhfPlugin.setWorkArea(String area);`

- Get Work area (returns string number)

  `await UhfPlugin.getWorkArea;`

- Listen to tags status

  `UhfPlugin.tagsStatusStream.receiveBroadcastStream().listen(updateTags);`

  ```dart
     List<TagEpc> _data = [];
     void updateTags(dynamic result) {
      setState(() {
          _data = TagEpc.parseTags(result);
       });
     }
  ```
