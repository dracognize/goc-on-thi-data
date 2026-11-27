---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==

# Excalidraw Data

## Text Elements
con = sqlite3.connect(f)
mở/tạo tệp CSDL ^LBcbfnoG

con.execute(CREATE TABLE)
bảng test: a,b,c,d ^WZkSBvrj

con.commit()
lưu cấu trúc ^UDIh7yfJ

con.executemany(INSERT ?,?,?,?)
3 tuple → 3 hàng ^2o3gyrDO

con.commit()
lưu dữ liệu ^IUpkDyr7

cursor = con.execute(SELECT *) ^ren68K4T

rows = cursor.fetchall()
list tuple, gọi lại → [] ^pVJIqVLB

cursor.description
x[0] = tên cột a,b,c,d ^OkYRBMey

pd.DataFrame(rows, columns=...)
3 hàng × 4 cột ^XPvhsBkD

con.close()
giải phóng tài nguyên ^jxWkI9X7

OperationalError
bảng đã tồn tại ^dp4K8ffU

IntegrityError
trùng khóa / ràng buộc ^H3MB9n7I

Quên commit → thay đổi không vào tệp
Sau close → ProgrammingError ^oevbLJoL

truy vấn ^BS9UYJQT

chạy lần 2 ^ddLEG62H

vi phạm ^h84KpLMc

Theo dấu trạng thái: từ connect đến close ^QLKHu7qn

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
   "width": 320,
   "height": 100,
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
     "id": "eTOdoe5c"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "LBcbfnoG",
   "type": "text",
   "x": 10,
   "y": 30.0,
   "width": 300,
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
   "seed": 113971124,
   "version": 1,
   "versionNonce": 854001194,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "con = sqlite3.connect(f)\nmở/tạo tệp CSDL",
   "originalText": "con = sqlite3.connect(f)\nmở/tạo tệp CSDL",
   "fontSize": 16,
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
   "width": 320,
   "height": 100,
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
     "id": "eTOdoe5c"
    },
    {
     "type": "arrow",
     "id": "YEZAmggQ"
    },
    {
     "type": "arrow",
     "id": "msn9dLVI"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "WZkSBvrj",
   "type": "text",
   "x": 370,
   "y": 30.0,
   "width": 300,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "con.execute(CREATE TABLE)\nbảng test: a,b,c,d",
   "originalText": "con.execute(CREATE TABLE)\nbảng test: a,b,c,d",
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
   "x": 720,
   "y": 0,
   "width": 320,
   "height": 100,
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
     "id": "YEZAmggQ"
    },
    {
     "type": "arrow",
     "id": "zUvZ3gpm"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "UDIh7yfJ",
   "type": "text",
   "x": 730,
   "y": 30.0,
   "width": 300,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "con.commit()\nlưu cấu trúc",
   "originalText": "con.commit()\nlưu cấu trúc",
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
   "x": 1080,
   "y": 0,
   "width": 320,
   "height": 100,
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
     "id": "zUvZ3gpm"
    },
    {
     "type": "arrow",
     "id": "Z32JgdPI"
    },
    {
     "type": "arrow",
     "id": "9Gf2leMe"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "2o3gyrDO",
   "type": "text",
   "x": 1090,
   "y": 30.0,
   "width": 300,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "con.executemany(INSERT ?,?,?,?)\n3 tuple → 3 hàng",
   "originalText": "con.executemany(INSERT ?,?,?,?)\n3 tuple → 3 hàng",
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
   "x": 1440,
   "y": 0,
   "width": 320,
   "height": 100,
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
     "id": "Z32JgdPI"
    },
    {
     "type": "arrow",
     "id": "5dkyayq7"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "IUpkDyr7",
   "type": "text",
   "x": 1450,
   "y": 30.0,
   "width": 300,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "con.commit()\nlưu dữ liệu",
   "originalText": "con.commit()\nlưu dữ liệu",
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
   "x": 1440,
   "y": 300,
   "width": 320,
   "height": 100,
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
     "id": "GprQFnIi"
    },
    {
     "type": "arrow",
     "id": "5dkyayq7"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "ren68K4T",
   "type": "text",
   "x": 1450,
   "y": 340.0,
   "width": 300,
   "height": 20.0,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "cursor = con.execute(SELECT *)",
   "originalText": "cursor = con.execute(SELECT *)",
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
   "x": 1080,
   "y": 300,
   "width": 320,
   "height": 100,
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
    },
    {
     "type": "arrow",
     "id": "BAD3UdRP"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "pVJIqVLB",
   "type": "text",
   "x": 1090,
   "y": 330.0,
   "width": 300,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "rows = cursor.fetchall()\nlist tuple, gọi lại → []",
   "originalText": "rows = cursor.fetchall()\nlist tuple, gọi lại → []",
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
   "x": 720,
   "y": 300,
   "width": 320,
   "height": 100,
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
     "id": "BAD3UdRP"
    },
    {
     "type": "arrow",
     "id": "iBlrDp37"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "OkYRBMey",
   "type": "text",
   "x": 730,
   "y": 330.0,
   "width": 300,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "cursor.description\nx[0] = tên cột a,b,c,d",
   "originalText": "cursor.description\nx[0] = tên cột a,b,c,d",
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
   "x": 360,
   "y": 300,
   "width": 320,
   "height": 100,
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
     "id": "iBlrDp37"
    },
    {
     "type": "arrow",
     "id": "7W2pkAFE"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "XPvhsBkD",
   "type": "text",
   "x": 370,
   "y": 330.0,
   "width": 300,
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
   "seed": 13938522,
   "version": 1,
   "versionNonce": 1131247331,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "pd.DataFrame(rows, columns=...)\n3 hàng × 4 cột",
   "originalText": "pd.DataFrame(rows, columns=...)\n3 hàng × 4 cột",
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
   "x": 0,
   "y": 300,
   "width": 320,
   "height": 100,
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
     "id": "7W2pkAFE"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "jxWkI9X7",
   "type": "text",
   "x": 10,
   "y": 330.0,
   "width": 300,
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
   "seed": 2456274,
   "version": 1,
   "versionNonce": 1392239676,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "con.close()\ngiải phóng tài nguyên",
   "originalText": "con.close()\ngiải phóng tài nguyên",
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
   "x": 360,
   "y": -220,
   "width": 320,
   "height": 90,
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
     "id": "msn9dLVI"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "dp4K8ffU",
   "type": "text",
   "x": 370,
   "y": -195.0,
   "width": 300,
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
   "seed": 2087313122,
   "version": 1,
   "versionNonce": 297265481,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "OperationalError\nbảng đã tồn tại",
   "originalText": "OperationalError\nbảng đã tồn tại",
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
   "type": "rectangle",
   "x": 1080,
   "y": -220,
   "width": 320,
   "height": 90,
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
   "seed": 709214892,
   "version": 1,
   "versionNonce": 1138409540,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "H3MB9n7I"
    },
    {
     "type": "arrow",
     "id": "9Gf2leMe"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "H3MB9n7I",
   "type": "text",
   "x": 1090,
   "y": -195.0,
   "width": 300,
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
   "seed": 863937248,
   "version": 1,
   "versionNonce": 1338811291,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "IntegrityError\ntrùng khóa / ràng buộc",
   "originalText": "IntegrityError\ntrùng khóa / ràng buộc",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "WIXiiQE8",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "zQPxC5HC",
   "type": "rectangle",
   "x": 0,
   "y": 520,
   "width": 520,
   "height": 90,
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
   "seed": 519709080,
   "version": 1,
   "versionNonce": 1064746526,
   "isDeleted": false,
   "boundElements": [
    {
     "type": "text",
     "id": "oevbLJoL"
    }
   ],
   "updated": 1795724399003,
   "link": null,
   "locked": false
  },
  {
   "id": "oevbLJoL",
   "type": "text",
   "x": 10,
   "y": 545.0,
   "width": 500,
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
   "seed": 945826487,
   "version": 1,
   "versionNonce": 30884439,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "text": "Quên commit → thay đổi không vào tệp\nSau close → ProgrammingError",
   "originalText": "Quên commit → thay đổi không vào tệp\nSau close → ProgrammingError",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "middle",
   "containerId": "zQPxC5HC",
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "eTOdoe5c",
   "type": "arrow",
   "x": 326.0,
   "y": 50.0,
   "width": 28.0,
   "height": 0.0,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     28.0,
     0.0
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
   "id": "GprQFnIi",
   "type": "arrow",
   "x": 1434.0,
   "y": 350.0,
   "width": 28.0,
   "height": 0.0,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -28.0,
     0.0
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
   "id": "YEZAmggQ",
   "type": "arrow",
   "x": 686.0,
   "y": 50.0,
   "width": 28.0,
   "height": 0.0,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     28.0,
     0.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "TPSIAoCL",
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
   "id": "BAD3UdRP",
   "type": "arrow",
   "x": 1074.0,
   "y": 350.0,
   "width": 28.0,
   "height": 0.0,
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
   "updated": 1795724399003,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -28.0,
     0.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "PFz46PDj",
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
   "id": "zUvZ3gpm",
   "type": "arrow",
   "x": 1046.0,
   "y": 50.0,
   "width": 28.0,
   "height": 0.0,
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
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     28.0,
     0.0
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
   "id": "iBlrDp37",
   "type": "arrow",
   "x": 714.0,
   "y": 350.0,
   "width": 28.0,
   "height": 0.0,
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
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -28.0,
     0.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "oiGFfWd3",
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
   "id": "Z32JgdPI",
   "type": "arrow",
   "x": 1406.0,
   "y": 50.0,
   "width": 28.0,
   "height": 0.0,
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
   "seed": 63384489,
   "version": 1,
   "versionNonce": 400560568,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     28.0,
     0.0
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
   "id": "7W2pkAFE",
   "type": "arrow",
   "x": 354.0,
   "y": 350.0,
   "width": 28.0,
   "height": 0.0,
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
   "seed": 918037634,
   "version": 1,
   "versionNonce": 1722454918,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     -28.0,
     0.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "HqJ38aRU",
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
   "id": "5dkyayq7",
   "type": "arrow",
   "x": 1600.0,
   "y": 106.0,
   "width": 0.0,
   "height": 188.0,
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
   "seed": 1954246075,
   "version": 1,
   "versionNonce": 1225136115,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     0.0,
     188.0
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
   "id": "BS9UYJQT",
   "type": "text",
   "x": 1559.8,
   "y": 174.0,
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
   "seed": 2090237818,
   "version": 1,
   "versionNonce": 664847320,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "text": "truy vấn",
   "originalText": "truy vấn",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "msn9dLVI",
   "type": "arrow",
   "x": 520.0,
   "y": -6.0,
   "width": 0.0,
   "height": 118.0,
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
   "seed": 261810764,
   "version": 1,
   "versionNonce": 1346922427,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     0.0,
     -118.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "TPSIAoCL",
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
   "id": "ddLEG62H",
   "type": "text",
   "x": 471.0,
   "y": -91.0,
   "width": 98.0,
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
   "seed": 676168422,
   "version": 1,
   "versionNonce": 244295905,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "text": "chạy lần 2",
   "originalText": "chạy lần 2",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "9Gf2leMe",
   "type": "arrow",
   "x": 1240.0,
   "y": -6.0,
   "width": 0.0,
   "height": 118.0,
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
   "seed": 1010193047,
   "version": 1,
   "versionNonce": 1734202800,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "points": [
    [
     0,
     0
    ],
    [
     0.0,
     -118.0
    ]
   ],
   "lastCommittedPoint": null,
   "startBinding": {
    "elementId": "KmTecQoX",
    "focus": 0,
    "gap": 6
   },
   "endBinding": {
    "elementId": "WIXiiQE8",
    "focus": 0,
    "gap": 6
   },
   "startArrowhead": null,
   "endArrowhead": "arrow"
  },
  {
   "id": "h84KpLMc",
   "type": "text",
   "x": 1204.2,
   "y": -91.0,
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
   "seed": 352116053,
   "version": 1,
   "versionNonce": 1800557284,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "text": "vi phạm",
   "originalText": "vi phạm",
   "fontSize": 16,
   "fontFamily": 5,
   "textAlign": "center",
   "verticalAlign": "top",
   "containerId": null,
   "lineHeight": 1.25,
   "autoResize": true
  },
  {
   "id": "QLKHu7qn",
   "type": "text",
   "x": 0,
   "y": -320,
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
   "seed": 1349409435,
   "version": 1,
   "versionNonce": 1025148382,
   "isDeleted": false,
   "boundElements": [],
   "updated": 1795724399004,
   "link": null,
   "locked": false,
   "text": "Theo dấu trạng thái: từ connect đến close",
   "originalText": "Theo dấu trạng thái: từ connect đến close",
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