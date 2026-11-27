---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==

# Excalidraw Data

## Text Elements
customers
index 1, 2, 3, 4
name, gener, age ^LBcbfnoG

purchases
index 3, 4, 2
total_spent ^WZkSBvrj

scores
index 2, 3, 1
credit_score ^UDIh7yfJ

join='outer' (mặc định)
hợp nhãn {1, 2, 3, 4} ^2o3gyrDO

1 Alice: spent NaN, score 700
2 Bob: 3000, 650
3 Charlie: 5000, 720
4 Anna: 2000, NaN ^IUpkDyr7

join='inner'
giao {2, 3}: Bob, Charlie
không NaN ^ren68K4T

kết quả ^HqJ38aRU

nếu đổi join ^GWlG6g3O

concat(axis=1) căn theo NHÃN index, không theo vị trí (tr. 76–77) ^jxWkI9X7

%%
## Drawing
```json
{
 "type": "excalidraw",
 "version": 2,
 "source": "https://github.com/zsviczian/obsidian-excalidraw-plugin",
 "elements": [
  {
   "id": "OhbVrpoi",
   "type": "rectangle",
   "x": 0,
   "y": 0,
   "width": 300,
   "height": 130,
   "angle": 0,
   "strokeColor": "#1971c2",
   "backgroundColor": "#d0ebff",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 3
   },
   "seed": 440213416,
   "version": 1,
   "versionNonce": 373399427,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "LBcbfnoG"
    },
    {
     "type": "arrow",
     "id": "PFz46PDj"
    }
   ],
   "updated": 1795724253363,
   "link": null,
   "locked": false
  },
  {
   "id": "LBcbfnoG",
   "type": "text",
   "x": 10,
   "y": 27.5,
   "width": 280,
   "height": 75.0,
   "angle": 0,
   "strokeColor": "#1e1e1e",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 113971124,
   "version": 1,
   "versionNonce": 854001194,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "customers\nindex 1, 2, 3, 4\nname, gener, age",
   "originalText": "customers\nindex 1, 2, 3, 4\nname, gener, age",
   "fontSize": 20,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "OhbVrpoi",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "TPSIAoCL",
   "type": "rectangle",
   "x": 360,
   "y": 0,
   "width": 300,
   "height": 130,
   "angle": 0,
   "strokeColor": "#2f9e44",
   "backgroundColor": "#d3f9d8",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 3
   },
   "seed": 1194819985,
   "version": 1,
   "versionNonce": 27911968,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "WZkSBvrj"
    },
    {
     "type": "arrow",
     "id": "pVJIqVLB"
    }
   ],
   "updated": 1795724253363,
   "link": null,
   "locked": false
  },
  {
   "id": "WZkSBvrj",
   "type": "text",
   "x": 370,
   "y": 27.5,
   "width": 280,
   "height": 75.0,
   "angle": 0,
   "strokeColor": "#1e1e1e",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 924765564,
   "version": 1,
   "versionNonce": 1445662586,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "purchases\nindex 3, 4, 2\ntotal_spent",
   "originalText": "purchases\nindex 3, 4, 2\ntotal_spent",
   "fontSize": 20,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "TPSIAoCL",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "gfygw2wM",
   "type": "rectangle",
   "x": 720,
   "y": 0,
   "width": 300,
   "height": 130,
   "angle": 0,
   "strokeColor": "#6741d9",
   "backgroundColor": "#e5dbff",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 3
   },
   "seed": 1136108455,
   "version": 1,
   "versionNonce": 186618212,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "UDIh7yfJ"
    },
    {
     "type": "arrow",
     "id": "oiGFfWd3"
    }
   ],
   "updated": 1795724253363,
   "link": null,
   "locked": false
  },
  {
   "id": "UDIh7yfJ",
   "type": "text",
   "x": 730,
   "y": 27.5,
   "width": 280,
   "height": 75.0,
   "angle": 0,
   "strokeColor": "#1e1e1e",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 1259191106,
   "version": 1,
   "versionNonce": 1553210609,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "scores\nindex 2, 3, 1\ncredit_score",
   "originalText": "scores\nindex 2, 3, 1\ncredit_score",
   "fontSize": 20,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "gfygw2wM",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "KmTecQoX",
   "type": "rectangle",
   "x": 360,
   "y": 210,
   "width": 300,
   "height": 130,
   "angle": 0,
   "strokeColor": "#e67700",
   "backgroundColor": "#fff3bf",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 3
   },
   "seed": 1242911822,
   "version": 1,
   "versionNonce": 342703922,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "2o3gyrDO"
    },
    {
     "type": "arrow",
     "id": "PFz46PDj"
    },
    {
     "type": "arrow",
     "id": "pVJIqVLB"
    },
    {
     "type": "arrow",
     "id": "oiGFfWd3"
    },
    {
     "type": "arrow",
     "id": "OkYRBMey"
    },
    {
     "type": "arrow",
     "id": "XPvhsBkD"
    }
   ],
   "updated": 1795724253363,
   "link": null,
   "locked": false
  },
  {
   "id": "2o3gyrDO",
   "type": "text",
   "x": 370,
   "y": 250.0,
   "width": 280,
   "height": 50.0,
   "angle": 0,
   "strokeColor": "#1e1e1e",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 1566942274,
   "version": 1,
   "versionNonce": 698594026,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "join='outer' (mặc định)\nhợp nhãn {1, 2, 3, 4}",
   "originalText": "join='outer' (mặc định)\nhợp nhãn {1, 2, 3, 4}",
   "fontSize": 20,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "KmTecQoX",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "xwnQrS7R",
   "type": "rectangle",
   "x": -20,
   "y": 420,
   "width": 370,
   "height": 140,
   "angle": 0,
   "strokeColor": "#0c8599",
   "backgroundColor": "#c3fae8",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 3
   },
   "seed": 306671448,
   "version": 1,
   "versionNonce": 735034882,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "IUpkDyr7"
    },
    {
     "type": "arrow",
     "id": "OkYRBMey"
    }
   ],
   "updated": 1795724253363,
   "link": null,
   "locked": false
  },
  {
   "id": "IUpkDyr7",
   "type": "text",
   "x": -10,
   "y": 440.0,
   "width": 350,
   "height": 100.0,
   "angle": 0,
   "strokeColor": "#1e1e1e",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 943239975,
   "version": 1,
   "versionNonce": 1392783744,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "1 Alice: spent NaN, score 700\n2 Bob: 3000, 650\n3 Charlie: 5000, 720\n4 Anna: 2000, NaN",
   "originalText": "1 Alice: spent NaN, score 700\n2 Bob: 3000, 650\n3 Charlie: 5000, 720\n4 Anna: 2000, NaN",
   "fontSize": 20,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "xwnQrS7R",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "1XXdo0cZ",
   "type": "rectangle",
   "x": 720,
   "y": 420,
   "width": 315,
   "height": 130,
   "angle": 0,
   "strokeColor": "#d9480f",
   "backgroundColor": "#ffe8cc",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 3
   },
   "seed": 1354860541,
   "version": 1,
   "versionNonce": 1722989660,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "ren68K4T"
    },
    {
     "type": "arrow",
     "id": "XPvhsBkD"
    }
   ],
   "updated": 1795724253363,
   "link": null,
   "locked": false
  },
  {
   "id": "ren68K4T",
   "type": "text",
   "x": 730,
   "y": 447.5,
   "width": 295,
   "height": 75.0,
   "angle": 0,
   "strokeColor": "#1e1e1e",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 1351531224,
   "version": 1,
   "versionNonce": 913224048,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "join='inner'\ngiao {2, 3}: Bob, Charlie\nkhông NaN",
   "originalText": "join='inner'\ngiao {2, 3}: Bob, Charlie\nkhông NaN",
   "fontSize": 20,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "1XXdo0cZ",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "PFz46PDj",
   "type": "arrow",
   "x": 271.7142857142857,
   "y": 136.0,
   "width": 116.57142857142856,
   "height": 68.0,
   "angle": 0,
   "strokeColor": "#495057",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 2
   },
   "seed": 1137651679,
   "version": 1,
   "versionNonce": 599707678,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     116.57142857142856,
     68.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "KmTecQoX",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "pVJIqVLB",
   "type": "arrow",
   "x": 510.0,
   "y": 136.0,
   "width": 0.0,
   "height": 68.0,
   "angle": 0,
   "strokeColor": "#495057",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 2
   },
   "seed": 1715412120,
   "version": 1,
   "versionNonce": 1554762904,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     0.0,
     68.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "TPSIAoCL",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "KmTecQoX",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "oiGFfWd3",
   "type": "arrow",
   "x": 748.2857142857142,
   "y": 136.0,
   "width": 116.57142857142844,
   "height": 68.0,
   "angle": 0,
   "strokeColor": "#495057",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 2
   },
   "seed": 470939446,
   "version": 1,
   "versionNonce": 656448480,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -116.57142857142844,
     68.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "gfygw2wM",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "KmTecQoX",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "OkYRBMey",
   "type": "arrow",
   "x": 396.06976744186045,
   "y": 346.0,
   "width": 109.11627906976742,
   "height": 68.0,
   "angle": 0,
   "strokeColor": "#495057",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 2
   },
   "seed": 1639042339,
   "version": 1,
   "versionNonce": 2010258947,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -109.11627906976742,
     68.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "KmTecQoX",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "xwnQrS7R",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "HqJ38aRU",
   "type": "text",
   "x": 305.71162790697673,
   "y": 354.0,
   "width": 71.60000000000001,
   "height": 22,
   "angle": 0,
   "strokeColor": "#495057",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 491995980,
   "version": 1,
   "versionNonce": 1146005449,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "kết quả",
   "originalText": "kết quả",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "XPvhsBkD",
   "type": "arrow",
   "x": 634.25,
   "y": 346.0,
   "width": 119.0,
   "height": 68.0,
   "angle": 0,
   "strokeColor": "#495057",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "dashed",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": {
    "type": 2
   },
   "seed": 13938522,
   "version": 1,
   "versionNonce": 1131247331,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     119.0,
     68.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "KmTecQoX",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "1XXdo0cZ",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "GWlG6g3O",
   "type": "text",
   "x": 635.95,
   "y": 354.0,
   "width": 115.60000000000001,
   "height": 22,
   "angle": 0,
   "strokeColor": "#495057",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 1281810601,
   "version": 1,
   "versionNonce": 854316682,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "nếu đổi join",
   "originalText": "nếu đổi join",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "jxWkI9X7",
   "type": "text",
   "x": 0,
   "y": -90,
   "width": 939.5000000000001,
   "height": 32.5,
   "angle": 0,
   "strokeColor": "#1e1e1e",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 2456274,
   "version": 1,
   "versionNonce": 1392239676,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724253363,
   "link": null,
   "locked": false,
   "text": "concat(axis=1) căn theo NHÃN index, không theo vị trí (tr. 76–77)",
   "originalText": "concat(axis=1) căn theo NHÃN index, không theo vị trí (tr. 76–77)",
   "fontSize": 26,
   "fontFamily": 5,
   "textAlign": "left",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  }
 ],
 "appState": {
  "gridSize": null,
  "viewBackgroundColor": "#ffffff"
 },
 "files": {}
}
```
%%