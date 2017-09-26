# qrcode
pure javascript qrcode generator



this is froked from https://github.com/kazuhikoarase/qrcode-generator .

if you want know more, you should read [kazuhikoarase‘s](https://github.com/kazuhikoarase) project.



## Basic Usages



```
import { extQr } from './qrcode'

var typeNumber = 4;
var errorCorrectionLevel = 'L';
var qr = extQr(typeNumber, errorCorrectionLevel);
qr.addData('Hi!');
qr.make();
qr.createImgTag(); // this is a base64 data
```





## API Documentation

### QRCodeFactory

#### qrcode(typeNumber, errorCorrectionLevel) => `QRCode`

Create a QRCode Object.

| Param                | Type     | Description                              |
| -------------------- | -------- | ---------------------------------------- |
| typeNumber           | `number` | Type number (1 ~ 40)                     |
| errorCorrectionLevel | `string` | Error correction level ('L', 'M', 'Q', 'H') |

#### qrcode.stringToBytes(s) : `number[]`

Encodes a string into an array of number(byte) using any charset. This function is used by internal. Overwrite this function to encode using a multibyte charset.

| Param | Type     | Description      |
| ----- | -------- | ---------------- |
| s     | `string` | string to encode |

### QRCode

#### addData(data, mode) => `void`

Add a data to encode.

| Param | Type     | Description                              |
| ----- | -------- | ---------------------------------------- |
| data  | `string` | string to encode                         |
| mode  | `string` | Mode ('Numeric', 'Alphanumeric', 'Byte'(default), 'Kanji') |

#### make() => `void`

Make a QR Code.

#### getModuleCount() => `number`

The number of modules(cells) for each orientation. *[Note] call make() before this function.*

#### isDark(row, col) => `boolean`

The module at row and col is dark or not. *[Note] call make() before this function.*

| Param | Type     | Description         |
| ----- | -------- | ------------------- |
| row   | `number` | 0 ~ moduleCount - 1 |
| col   | `number` | 0 ~ moduleCount - 1 |

#### createImgTag(cellSize, margin) => `string`

#### createSvgTag(cellSize, margin) => `string`

#### createTableTag(cellSize, margin) => `string`

Helper functions for HTML. *[Note] call make() before these functions.*

| Param    | Type     | Description           |
| -------- | -------- | --------------------- |
| cellSize | `number` | default: 2            |
| margin   | `number` | default: cellSize * 4 |

-- The word 'QR Code' is registered trademark of DENSO WAVE INCORPORATED 
[http://www.denso-wave.com/qrcode/faqpatent-e.html](http://www.denso-wave.com/qrcode/faqpatent-e.html)
