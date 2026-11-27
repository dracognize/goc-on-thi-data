---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==

# Excalidraw Data

## Text Elements
Dữ liệu
nằm ở đâu? ^LBcbfnoG

CSV, văn bản có dấu tách
→ pd.read_csv(sep, header, ...) ^WZkSBvrj

Tách bằng tab
→ pd.read_table ^UDIh7yfJ

Cột độ rộng cố định
→ pd.read_fwf ^2o3gyrDO

Bảng đã copy
→ pd.read_clipboard ^IUpkDyr7

Excel nhiều sheet
→ pd.ExcelFile(...).parse
pd.read_excel ^ren68K4T

Chuỗi / tệp JSON
→ json.loads · pd.read_json ^pVJIqVLB

Bảng trong trang HTML
→ pd.read_html → list DataFrame ^OkYRBMey

XML, RSS feed
→ BeautifulSoup(..., 'xml')
pd.read_xml ^XPvhsBkD

API web
→ requests.get → status_code
→ .json() → DataFrame ^jxWkI9X7

Cơ sở dữ liệu SQL
→ sqlite3 / SQLAlchemy
pd.read_sql ^dp4K8ffU

Chọn hàm đọc theo nguồn dữ liệu (tr. 119) ^Z32JgdPI

Tệp văn bản / bảng tính ^7W2pkAFE

Dữ liệu có cấu trúc / mạng / CSDL ^5dkyayq7

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
   "type": "diamond",
   "x": 520,
   "y": 250,
   "width": 280,
   "height": 200,
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
   "roundness": null,
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
     "id": "WIXiiQE8"
    },
    {
     "type": "arrow",
     "id": "H3MB9n7I"
    },
    {
     "type": "arrow",
     "id": "zQPxC5HC"
    },
    {
     "type": "arrow",
     "id": "oevbLJoL"
    },
    {
     "type": "arrow",
     "id": "eTOdoe5c"
    },
    {
     "type": "arrow",
     "id": "GprQFnIi"
    },
    {
     "type": "arrow",
     "id": "YEZAmggQ"
    },
    {
     "type": "arrow",
     "id": "BAD3UdRP"
    },
    {
     "type": "arrow",
     "id": "zUvZ3gpm"
    },
    {
     "type": "arrow",
     "id": "iBlrDp37"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "LBcbfnoG",
   "type": "text",
   "x": 530,
   "y": 322.5,
   "width": 260,
   "height": 55.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Dữ liệu\nnằm ở đâu?",
   "originalText": "Dữ liệu\nnằm ở đâu?",
   "fontSize": 22,
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
   "x": 0,
   "y": 0,
   "width": 380,
   "height": 110,
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
     "id": "WIXiiQE8"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "WZkSBvrj",
   "type": "text",
   "x": 10,
   "y": 35.0,
   "width": 360,
   "height": 40.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "CSV, văn bản có dấu tách\n→ pd.read_csv(sep, header, ...)",
   "originalText": "CSV, văn bản có dấu tách\n→ pd.read_csv(sep, header, ...)",
   "fontSize": 16,
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
   "y": 150,
   "width": 380,
   "height": 110,
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
     "id": "H3MB9n7I"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "UDIh7yfJ",
   "type": "text",
   "x": 10,
   "y": 185.0,
   "width": 360,
   "height": 40.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Tách bằng tab\n→ pd.read_table",
   "originalText": "Tách bằng tab\n→ pd.read_table",
   "fontSize": 16,
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
   "x": 0,
   "y": 300,
   "width": 380,
   "height": 110,
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
     "id": "zQPxC5HC"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "2o3gyrDO",
   "type": "text",
   "x": 10,
   "y": 335.0,
   "width": 360,
   "height": 40.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Cột độ rộng cố định\n→ pd.read_fwf",
   "originalText": "Cột độ rộng cố định\n→ pd.read_fwf",
   "fontSize": 16,
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
   "x": 0,
   "y": 450,
   "width": 380,
   "height": 110,
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
     "id": "oevbLJoL"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "IUpkDyr7",
   "type": "text",
   "x": 10,
   "y": 485.0,
   "width": 360,
   "height": 40.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Bảng đã copy\n→ pd.read_clipboard",
   "originalText": "Bảng đã copy\n→ pd.read_clipboard",
   "fontSize": 16,
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
   "x": 0,
   "y": 600,
   "width": 380,
   "height": 110,
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
     "id": "eTOdoe5c"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "ren68K4T",
   "type": "text",
   "x": 10,
   "y": 625.0,
   "width": 360,
   "height": 60.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Excel nhiều sheet\n→ pd.ExcelFile(...).parse\npd.read_excel",
   "originalText": "Excel nhiều sheet\n→ pd.ExcelFile(...).parse\npd.read_excel",
   "fontSize": 16,
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
   "x": 940,
   "y": 0,
   "width": 380,
   "height": 110,
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
     "id": "GprQFnIi"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "pVJIqVLB",
   "type": "text",
   "x": 950,
   "y": 35.0,
   "width": 360,
   "height": 40.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Chuỗi / tệp JSON\n→ json.loads · pd.read_json",
   "originalText": "Chuỗi / tệp JSON\n→ json.loads · pd.read_json",
   "fontSize": 16,
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
   "x": 940,
   "y": 150,
   "width": 380,
   "height": 110,
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
     "id": "YEZAmggQ"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "OkYRBMey",
   "type": "text",
   "x": 950,
   "y": 185.0,
   "width": 360,
   "height": 40.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Bảng trong trang HTML\n→ pd.read_html → list DataFrame",
   "originalText": "Bảng trong trang HTML\n→ pd.read_html → list DataFrame",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "oiGFfWd3",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "HqJ38aRU",
   "type": "rectangle",
   "x": 940,
   "y": 300,
   "width": 380,
   "height": 110,
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
   "seed": 491995980,
   "version": 1,
   "versionNonce": 1146005449,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "XPvhsBkD"
    },
    {
     "type": "arrow",
     "id": "BAD3UdRP"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "XPvhsBkD",
   "type": "text",
   "x": 950,
   "y": 325.0,
   "width": 360,
   "height": 60.0,
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
   "seed": 13938522,
   "version": 1,
   "versionNonce": 1131247331,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "XML, RSS feed\n→ BeautifulSoup(..., 'xml')\npd.read_xml",
   "originalText": "XML, RSS feed\n→ BeautifulSoup(..., 'xml')\npd.read_xml",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "HqJ38aRU",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "GWlG6g3O",
   "type": "rectangle",
   "x": 940,
   "y": 450,
   "width": 380,
   "height": 110,
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
   "seed": 1281810601,
   "version": 1,
   "versionNonce": 854316682,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "jxWkI9X7"
    },
    {
     "type": "arrow",
     "id": "zUvZ3gpm"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "jxWkI9X7",
   "type": "text",
   "x": 950,
   "y": 475.0,
   "width": 360,
   "height": 60.0,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "API web\n→ requests.get → status_code\n→ .json() → DataFrame",
   "originalText": "API web\n→ requests.get → status_code\n→ .json() → DataFrame",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "GWlG6g3O",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "Fbh7x41Z",
   "type": "rectangle",
   "x": 940,
   "y": 600,
   "width": 380,
   "height": 110,
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
   "seed": 1320763136,
   "version": 1,
   "versionNonce": 1028439864,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "dp4K8ffU"
    },
    {
     "type": "arrow",
     "id": "iBlrDp37"
    }
   ],
   "updated": 1795724399024,
   "link": null,
   "locked": false
  },
  {
   "id": "dp4K8ffU",
   "type": "text",
   "x": 950,
   "y": 625.0,
   "width": 360,
   "height": 60.0,
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
   "seed": 2087313122,
   "version": 1,
   "versionNonce": 297265481,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Cơ sở dữ liệu SQL\n→ sqlite3 / SQLAlchemy\npd.read_sql",
   "originalText": "Cơ sở dữ liệu SQL\n→ sqlite3 / SQLAlchemy\npd.read_sql",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "Fbh7x41Z",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "WIXiiQE8",
   "type": "arrow",
   "x": 514.0,
   "y": 258.36170212765956,
   "width": 226.81355932203394,
   "height": 142.36170212765956,
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
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -226.81355932203394,
     -142.36170212765956
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "TPSIAoCL",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "H3MB9n7I",
   "type": "arrow",
   "x": 514.0,
   "y": 304.95744680851067,
   "width": 128.0,
   "height": 39.48936170212767,
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
   "seed": 863937248,
   "version": 1,
   "versionNonce": 1338811291,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -128.0,
     -39.48936170212767
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
   "id": "zQPxC5HC",
   "type": "arrow",
   "x": 514.0,
   "y": 351.5531914893617,
   "width": 128.0,
   "height": 1.3617021276595551,
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
   "seed": 519709080,
   "version": 1,
   "versionNonce": 1064746526,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -128.0,
     1.3617021276595551
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
   "id": "oevbLJoL",
   "type": "arrow",
   "x": 514.0,
   "y": 398.1489361702128,
   "width": 139.0322580645161,
   "height": 45.85106382978722,
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
   "seed": 945826487,
   "version": 1,
   "versionNonce": 30884439,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -139.0322580645161,
     45.85106382978722
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
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
   "id": "eTOdoe5c",
   "type": "arrow",
   "x": 514.0,
   "y": 444.74468085106383,
   "width": 230.0,
   "height": 149.25531914893617,
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
   "seed": 1419179581,
   "version": 1,
   "versionNonce": 304330004,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -230.0,
     149.25531914893617
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
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
   "id": "GprQFnIi",
   "type": "arrow",
   "x": 806.0,
   "y": 258.36170212765956,
   "width": 226.81355932203383,
   "height": 142.36170212765956,
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
   "seed": 2030106618,
   "version": 1,
   "versionNonce": 1043665193,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     226.81355932203383,
     -142.36170212765956
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
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
   "id": "YEZAmggQ",
   "type": "arrow",
   "x": 806.0,
   "y": 304.95744680851067,
   "width": 128.0,
   "height": 39.48936170212767,
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
   "seed": 1851350740,
   "version": 1,
   "versionNonce": 1521696480,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     128.0,
     -39.48936170212767
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
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
   "id": "BAD3UdRP",
   "type": "arrow",
   "x": 806.0,
   "y": 351.5531914893617,
   "width": 128.0,
   "height": 1.3617021276595551,
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
   "seed": 422701551,
   "version": 1,
   "versionNonce": 260329456,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     128.0,
     1.3617021276595551
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "HqJ38aRU",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "zUvZ3gpm",
   "type": "arrow",
   "x": 806.0,
   "y": 398.1489361702128,
   "width": 139.0322580645161,
   "height": 45.85106382978722,
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
   "seed": 816941040,
   "version": 1,
   "versionNonce": 1926780542,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     139.0322580645161,
     45.85106382978722
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "GWlG6g3O",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "iBlrDp37",
   "type": "arrow",
   "x": 806.0,
   "y": 444.74468085106383,
   "width": 230.0,
   "height": 149.25531914893617,
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
   "seed": 323775635,
   "version": 1,
   "versionNonce": 1903232053,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     230.0,
     149.25531914893617
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "OhbVrpoi",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "Fbh7x41Z",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "Z32JgdPI",
   "type": "text",
   "x": 0,
   "y": -90,
   "width": 596.3000000000001,
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
   "seed": 63384489,
   "version": 1,
   "versionNonce": 400560568,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Chọn hàm đọc theo nguồn dữ liệu (tr. 119)",
   "originalText": "Chọn hàm đọc theo nguồn dữ liệu (tr. 119)",
   "fontSize": 26,
   "fontFamily": 5,
   "textAlign": "left",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "7W2pkAFE",
   "type": "text",
   "x": 0,
   "y": -40,
   "width": 237.70000000000002,
   "height": 22.5,
   "angle": 0,
   "strokeColor": "#1971c2",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 918037634,
   "version": 1,
   "versionNonce": 1722454918,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Tệp văn bản / bảng tính",
   "originalText": "Tệp văn bản / bảng tính",
   "fontSize": 18,
   "fontFamily": 5,
   "textAlign": "left",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "5dkyayq7",
   "type": "text",
   "x": 940,
   "y": -40,
   "width": 336.70000000000005,
   "height": 22.5,
   "angle": 0,
   "strokeColor": "#2f9e44",
   "backgroundColor": "transparent",
   "fillStyle": "solid",
   "strokeWidth": 2,
   "strokeStyle": "solid",
   "roughness": 1,
   "opacity": 100,
   "groupIds": [],
   "frameId": null,
   "roundness": null,
   "seed": 1954246075,
   "version": 1,
   "versionNonce": 1225136115,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399024,
   "link": null,
   "locked": false,
   "text": "Dữ liệu có cấu trúc / mạng / CSDL",
   "originalText": "Dữ liệu có cấu trúc / mạng / CSDL",
   "fontSize": 18,
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