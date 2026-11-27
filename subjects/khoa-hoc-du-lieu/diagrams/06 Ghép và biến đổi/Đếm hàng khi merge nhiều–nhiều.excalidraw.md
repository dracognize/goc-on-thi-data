---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==

# Excalidraw Data

## Text Elements
purchases (trái)
Alice ×2
Bob ×1
Charlie ×2 ^LBcbfnoG

favorites (phải)
Alice ×2
Bob ×1
Charlie ×1 ^WZkSBvrj

Alice: 2 × 2 = 4 ^UDIh7yfJ

Bob: 1 × 1 = 1 ^2o3gyrDO

Charlie: 2 × 1 = 2 ^IUpkDyr7

inner = 4 + 1 + 2 = 7 hàng
mỗi khóa: n_trái × n_phải ^ren68K4T

left/outer: cộng thêm
hàng của khóa không khớp ^pVJIqVLB

Phòng nhân hàng:
validate='many_to_one' ^OkYRBMey

đếm khóa ^XPvhsBkD

đếm khóa ^jxWkI9X7

merge(purchases, favorites, on='customer') ra bao nhiêu hàng? ^oevbLJoL

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
   "height": 140,
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
     "id": "HqJ38aRU"
    }
   ],
   "updated": 1795724244230,
   "link": null,
   "locked": false
  },
  {
   "id": "LBcbfnoG",
   "type": "text",
   "x": 10,
   "y": 20.0,
   "width": 280,
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
   "seed": 113971124,
   "version": 1,
   "versionNonce": 854001194,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "purchases (trái)\nAlice ×2\nBob ×1\nCharlie ×2",
   "originalText": "purchases (trái)\nAlice ×2\nBob ×1\nCharlie ×2",
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
   "x": 720,
   "y": 0,
   "width": 300,
   "height": 140,
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
     "id": "GWlG6g3O"
    }
   ],
   "updated": 1795724244230,
   "link": null,
   "locked": false
  },
  {
   "id": "WZkSBvrj",
   "type": "text",
   "x": 730,
   "y": 20.0,
   "width": 280,
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
   "seed": 924765564,
   "version": 1,
   "versionNonce": 1445662586,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "favorites (phải)\nAlice ×2\nBob ×1\nCharlie ×1",
   "originalText": "favorites (phải)\nAlice ×2\nBob ×1\nCharlie ×1",
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
   "x": 0,
   "y": 200,
   "width": 300,
   "height": 110,
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
     "id": "HqJ38aRU"
    },
    {
     "type": "arrow",
     "id": "Fbh7x41Z"
    }
   ],
   "updated": 1795724244230,
   "link": null,
   "locked": false
  },
  {
   "id": "UDIh7yfJ",
   "type": "text",
   "x": 10,
   "y": 242.5,
   "width": 280,
   "height": 25.0,
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
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "Alice: 2 × 2 = 4",
   "originalText": "Alice: 2 × 2 = 4",
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
   "y": 200,
   "width": 300,
   "height": 110,
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
     "id": "dp4K8ffU"
    }
   ],
   "updated": 1795724244230,
   "link": null,
   "locked": false
  },
  {
   "id": "2o3gyrDO",
   "type": "text",
   "x": 370,
   "y": 242.5,
   "width": 280,
   "height": 25.0,
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
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "Bob: 1 × 1 = 1",
   "originalText": "Bob: 1 × 1 = 1",
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
   "x": 720,
   "y": 200,
   "width": 300,
   "height": 110,
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
     "id": "GWlG6g3O"
    },
    {
     "type": "arrow",
     "id": "WIXiiQE8"
    }
   ],
   "updated": 1795724244230,
   "link": null,
   "locked": false
  },
  {
   "id": "IUpkDyr7",
   "type": "text",
   "x": 730,
   "y": 242.5,
   "width": 280,
   "height": 25.0,
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
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "Charlie: 2 × 1 = 2",
   "originalText": "Charlie: 2 × 1 = 2",
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
   "x": 360,
   "y": 400,
   "width": 326,
   "height": 110,
   "angle": 0,
   "strokeColor": "#c92a2a",
   "backgroundColor": "#ffe3e3",
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
     "id": "Fbh7x41Z"
    },
    {
     "type": "arrow",
     "id": "dp4K8ffU"
    },
    {
     "type": "arrow",
     "id": "WIXiiQE8"
    },
    {
     "type": "arrow",
     "id": "H3MB9n7I"
    },
    {
     "type": "arrow",
     "id": "zQPxC5HC"
    }
   ],
   "updated": 1795724244230,
   "link": null,
   "locked": false
  },
  {
   "id": "ren68K4T",
   "type": "text",
   "x": 370,
   "y": 430.0,
   "width": 306,
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
   "seed": 1351531224,
   "version": 1,
   "versionNonce": 913224048,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "inner = 4 + 1 + 2 = 7 hàng\nmỗi khóa: n_trái × n_phải",
   "originalText": "inner = 4 + 1 + 2 = 7 hàng\nmỗi khóa: n_trái × n_phải",
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
   "type": "rectangle",
   "x": 0,
   "y": 600,
   "width": 304,
   "height": 110,
   "angle": 0,
   "strokeColor": "#495057",
   "backgroundColor": "#f1f3f5",
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
   "seed": 1137651679,
   "version": 1,
   "versionNonce": 599707678,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "pVJIqVLB"
    },
    {
     "type": "arrow",
     "id": "H3MB9n7I"
    }
   ],
   "updated": 1795724244230,
   "link": null,
   "locked": false
  },
  {
   "id": "pVJIqVLB",
   "type": "text",
   "x": 10,
   "y": 630.0,
   "width": 284,
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
   "seed": 1715412120,
   "version": 1,
   "versionNonce": 1554762904,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "left/outer: cộng thêm\nhàng của khóa không khớp",
   "originalText": "left/outer: cộng thêm\nhàng của khóa không khớp",
   "fontSize": 20,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "PFz46PDj",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "oiGFfWd3",
   "type": "rectangle",
   "x": 720,
   "y": 600,
   "width": 300,
   "height": 110,
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
   "seed": 470939446,
   "version": 1,
   "versionNonce": 656448480,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "OkYRBMey"
    },
    {
     "type": "arrow",
     "id": "zQPxC5HC"
    }
   ],
   "updated": 1795724244230,
   "link": null,
   "locked": false
  },
  {
   "id": "OkYRBMey",
   "type": "text",
   "x": 730,
   "y": 630.0,
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
   "seed": 1639042339,
   "version": 1,
   "versionNonce": 2010258947,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "Phòng nhân hàng:\nvalidate='many_to_one'",
   "originalText": "Phòng nhân hàng:\nvalidate='many_to_one'",
   "fontSize": 20,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "oiGFfWd3",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "HqJ38aRU",
   "type": "arrow",
   "x": 150.0,
   "y": 146.0,
   "width": 0.0,
   "height": 48.0,
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
   "seed": 491995980,
   "version": 1,
   "versionNonce": 1146005449,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     0.0,
     48.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "gfygw2wM",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "XPvhsBkD",
   "type": "text",
   "x": 109.8,
   "y": 144.0,
   "width": 80.4,
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
   "seed": 13938522,
   "version": 1,
   "versionNonce": 1131247331,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "đếm khóa",
   "originalText": "đếm khóa",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "GWlG6g3O",
   "type": "arrow",
   "x": 870.0,
   "y": 146.0,
   "width": 0.0,
   "height": 48.0,
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
   "seed": 1281810601,
   "version": 1,
   "versionNonce": 854316682,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     0.0,
     48.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "TPSIAoCL",
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
   "id": "jxWkI9X7",
   "type": "text",
   "x": 829.8,
   "y": 144.0,
   "width": 80.4,
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
   "seed": 2456274,
   "version": 1,
   "versionNonce": 1392239676,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "đếm khóa",
   "originalText": "đếm khóa",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "Fbh7x41Z",
   "type": "arrow",
   "x": 263.765,
   "y": 316.0,
   "width": 145.47000000000003,
   "height": 78.0,
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
   "seed": 1320763136,
   "version": 1,
   "versionNonce": 1028439864,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     145.47000000000003,
     78.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "gfygw2wM",
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
   "id": "dp4K8ffU",
   "type": "arrow",
   "x": 513.965,
   "y": 316.0,
   "width": 5.069999999999936,
   "height": 78.0,
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
   "seed": 2087313122,
   "version": 1,
   "versionNonce": 297265481,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     5.069999999999936,
     78.0
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
   "id": "WIXiiQE8",
   "type": "arrow",
   "x": 764.165,
   "y": 316.0,
   "width": 135.32999999999993,
   "height": 78.0,
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
   "seed": 709214892,
   "version": 1,
   "versionNonce": 1138409540,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -135.32999999999993,
     78.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "xwnQrS7R",
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
   "id": "H3MB9n7I",
   "type": "arrow",
   "x": 409.845,
   "y": 516.0,
   "width": 144.69000000000005,
   "height": 78.0,
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
   "seed": 863937248,
   "version": 1,
   "versionNonce": 1338811291,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -144.69000000000005,
     78.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "1XXdo0cZ",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "PFz46PDj",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "zQPxC5HC",
   "type": "arrow",
   "x": 628.835,
   "y": 516.0,
   "width": 135.32999999999993,
   "height": 78.0,
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
   "seed": 519709080,
   "version": 1,
   "versionNonce": 1064746526,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     135.32999999999993,
     78.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "1XXdo0cZ",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "oiGFfWd3",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "oevbLJoL",
   "type": "text",
   "x": 0,
   "y": -90,
   "width": 882.3000000000001,
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
   "seed": 945826487,
   "version": 1,
   "versionNonce": 30884439,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724244230,
   "link": null,
   "locked": false,
   "text": "merge(purchases, favorites, on='customer') ra bao nhiêu hàng?",
   "originalText": "merge(purchases, favorites, on='customer') ra bao nhiêu hàng?",
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