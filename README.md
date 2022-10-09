# uhf_plugin

A flutter plugin for UHF type C66 to read UHF Cards. This was forked from the C72 plugin created by amorenew.

I included the newer API version from Chainway and updated for the latest version of Flutter (Oct 2022).

The README has not been updated apart from this top section.

#### Library Pub link

https://pub.dev/packages/uhf_plugin

### Getting Started

- Import the library:
  `import 'package:uhf_c66_plugin/uhf_c66_plugin.dart';`

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

- Set Power level (5 dBm : 30 dBm use string numbers)

  `await UhfPlugin.setPowerLevel;`

- Set Work area
  Area Values { "1", "2" 4", "8", "22", "50", "51", "52", "128"}
  `await UhfPlugin.setWorkArea;`

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
