# Train Data

----

## Download Datasets

The [Learner Notebook](../Learner.ipynb) expects it's train data to be located here. The easiest way is to download the data from here and place the json files directly into this folder:

* https://the-cake-is-a-lie.net/nextcloud/index.php/s/MmXFYj6mGoMQoJN

## How we created this dataset

* **NOTE**: we used the json processor [jq](https://stedolan.github.io/jq/) in some of our bash scripts!

we downloaded archieved twitter datasets from November and December of 2017 from here: https://archive.org/details/archiveteam-twitter-stream-2017-11

in a first step we filtered out messages containing no emojis using the self written [twitter2messages.sh](../../Tools/twitter2messages.sh) script for each single extracted tar-archive folder. The result is a single json file for each day, this intermediate result can also be downloaded here: https://the-cake-is-a-lie.net/nextcloud/index.php/s/s2c9edATidsMHZr

In the next step we did more preprocessing by removing urls, usernames and hashtags and adding emojis as new labeling json key by performing the following unix-bash commands:

```bash
# environment variable containing all emojis:
export elist='🀄🧱🧲🧳🧴🧵🧶🃏🤐🤑🤒🤓🤔🤕🤖🤗🤘🤙🤚🤛🤜🤝🤞🤟🤠🤡🤢🤣🤤🤥🤦🤧🤨🤩🤪🤫🤬🤭🤮🤯🤰🤱🤲🤳🤴🤵🤶🤷🤸🤹🤺🤼🤽🤾🥀🥁🥂🥃🥄🥅🥇🥈🥉🥊🥋🥌🥍🥎🥏🥐🥑🥒🥓🥔🥕🥖🥗🥘🥙🥚🥛🥜🥝🥞🥟🥠🥡🥢🥣🥤🥥🥦🥧🥨🥩🥪🥫🥬🥭🥮🥯🥰🧬🧭🥳🥴🥵🥶🧮🥺🧯🥼🥽🥾🥿🦀🦁🦂🦃🦄🦅🦆🦇🦈🦉🦊🦋🦌🦍🆎🦎🦏🆑🆒🆓🆔🆕🆖🆗🆘🆙🆚🦒🦓🦔🦕🦖🦗🦘🦙🦚🦛🦜🦝🦞🦟🦠🦡🦢🧸🦰🦱🦲🦳🦴🦵🦶🦷🦸🦹🧀🧁🧂🧐🧑🧒🧓🧔🧕🧖🧗🧘🧙🧚🧛🧜🧝🧞🧟🧠🧡🧢🧣🧤🧥🇦🇧🇨🇩🇪🇫🇬🇭🇮🇯🇰🇱🇲🇳🇴🇵🇶🇷🇸🇹🇺🇻🇼🇽🇾🇿🧷🈁🧹🧺🧻🧼🧽🧾🧿🈚🈯🈲🈳🈴🈵🈶🈸🈹🈺🉐🉑🌀🌁🌂🌃🌄🌅🌆🌇🌈🌉🌊🌋🌌🌍🌎🌏🌐🌑🌒🌓🌔🌕🌖🌗🌘🌙⌚⌛⬛⬜🌚🌛🌜🌝🌞🌟🌠🌭🌮🌯🌰🌱🌲🌳🌴🌵🌷🌸🌹🌺🌻🌼🌽🌾🌿🍀🍁🍂🍃🍄🍅🍆🍇🍈🍉🍊🍋🍌🍍🍎🍏⭐🍐🍑🍒🍓⭕🍔🍕🍖🍗🍘🍙🍚🍛🍜🍟🍝🍞🍠🍡🍤🍢🍣🍥🍦🍩🍧🍨🍪🍫🍮🍬🍭🍯🍰🍳🍱🍲🍴🍵🍸🍶🍷🍹🍺🍻🍼🍾🍿🎀🎁🎂🎃🎅🎄🎆🎈🎉🎊🎋🎌🎍🎇🎏🎐🎎🎑🎒🎓🎠🎡🎢🎣🎤🎥🎦🎧🎨🎩🎪🎫🎬🎭🎮🎯🎰🎱🎲🎳🎴🎵🎶🎷🎸🎹🎺🎻🎼🎽🎾🎿🏀🏁🏂🏃🏄🏅🏆🏇🏈🏉🏊🏏🏐🏑🏒🏓🏠🏡🏢🏣🏤🏥🏦🏧🏨🏩🏪🏫🏬🏭🏮🏯🏰⏩⏪⏫🏴⏬⏰⏳🏸🏹🏺🐀🐁🐂🐃🐄🐅🐆🐇🐈🐉🐊🐋🐌🐍🐎🐏🐐🐑🐒🐓🐔🐕🐖🐗🐘🐙🐚🐛🐜🐝🐞🐟🐠🐡🐢🐣🐤🐥🐦🐧🐨🐩🐪🐫🐬🐭🐮🐯🐰🐱🐲🐳🐴🐵🐶🐷🐸🐹🐺🐻🐼🐽🐾👀👂👃👄👅👆👇👈👉👊👋👌👍👎👏👐👑👒👓👔👕👖👗👘👙👚👛👜👝👞👟👠👡👢👣👤👥👦👧👨👩👪👫👬👭👮👯👰👱👲👳👴👵👶👷👸👹👺👻👼👽👾👿💀💁💂💃💄💅💆💇💈💉💊💋💌💍💎💏💐💑💒💓💔💕💖💗💘💙💚💛💜💝💞💟💠💡💢💣💤💥💦💧💨💩💪💫💬💭💮💯💰💱💲💳💴💵💶💷💸💹💺💻💼💽💾💿📀📁📂📃📄📅📆📇📈📉📊📋📌📍📎📏📐📑📒📓📔📕📖📗📘📙📚📛📜📝📞📟📠📡📢📣📤📥📦📧📨📩📪📫📬📭📮📯📰📱📲📳📴📵📶📷📸📹📺📻📼📿🔀🔁🔂🔃🔄🔅🔆🔇🔈🔉🔊🔋🔌🔍🔎🔏🔐🔑🔒🔓🔔🔕🔖🔗🔘🔙🔚🔛🔜🔝🔞🔟🔠🔡🔢🔣🔤🔥🔦🔧🔨🔩🔪🔫🔬🔭🔮🔯🔰🔱🔲🔳🔴🔵🔶🔷🔸🔹🔺🔻🔼🔽🕋🕌🕍🕎🕐🕑🕒🕓🕔🕕🕖🕗🕘🕙🕚🕛🕜🕝🕞🕟🕠🕡🕢🕣🕤🕥🕦🕧🕺🖕🖖🖤🗻🗼◽◾🗽🗾🗿😀😁😂😃😄😅😆😇😈😉😊😋😌😍😎😏😐😑☔☕😒😓😔😕😖😗😘😙😚😛😜😝😞😟😠😡😢😣😤😥😦😧😨😩😪😫😬😭😮😯😰😱😲😳😴😵😶😷😸😹😺😻😼😽😾😿🙀🙁🙂🙃♈♉♊♋♌♍♎♏♐♑♒♓🙋🙌🙍🙎🙏♿🚀🚁🚂🚃🚄🚅🚆🚇🚈🚉🚊🚋🚌🚍🚎🚏🚐🚑🚒⚓🚓🚔🚕🚖🚗🚘🚙🚚🚛🚜🚝🚞🚟⚡🚠🚡🚢🚣🚤🚥🚦🚧⚪⚫🚨🚩🚪🚫🚬🚭🚮🚯🚰🚱🚲🚳🚴🚵🚶🚷🚸⚽⚾🚹🚺🚻🚼🚽⛄⛅🚾🚿🛀🛁🛂🛃🛄🛅⛎🛌🛐🛑🛒⛔⛪🛫🛬⛲⛳🛴⛵🛵🛶🛷🛸⛺🛹⛽✅🧦🙄✊✋🙅🙆🙇🙈🧧🙉🙊✨🧨❌❎🧩❓❔❕❗🧪🧫➕➖➗🦐🦑➰➿🧰'

# loop over all files
for file in *.json
do
cat $file | jq '. | select (.lang == "en") | select(.text | startswith("RT ")| not)' | ./json_stream_filter.py ';RT;text;;' ';http[^ \\]*;text;;' ";[`echo $elist`];text;<EMOJI>;EMOJI" ";\\n;text;;" ';@[^ \\]+;text;<USER>;LINKED_USER' ';#[^ \\#]+;text;<HASHTAG>;HASHTAGS' | jq -s . > en/`basename $file | cut -d"-" -f3-5 | cut -d"." -f1`.json
done
```

* **Note**: Our helper script [json_stream_filter](../../Tools/json_stream_filter/) is expected to be in the current working directory

