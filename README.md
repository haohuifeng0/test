# test
# CloudHawk客户端与平台接口规范


---

### 1. 获取tracker信息 接口
URL: /api/v1/trackers

支持方法： GET， POST， PUT

支持客户端：Web,Android,IOS

**GET 方法**

功能描述： 获取账号终端详细信息列表

请求参数： 无

返回结果：
 
```json
{
  "status": 200, 
  "message": "Operation is successful.",
  "data": [
    {
      "labels": [ # 用户标签
        {
          "color": "#929103", # 标签颜色
          "name": "Car One",  # 标签名称
          "id": "3147bdb096ed4d60bda68906d765f9e1" # 标签的uuid
        }
      ],
      "fuel_highway": 8.0,
      "iccid": "89302720396911547656", # 终端类sim 卡的iccid号码
      "speed": 0,
      "id": "89302720396911547664",
      "last_stop": {  # 最近的停留信息
        "type": 0,    # 0:GPS定位；１:CELLID定位
        "name": "",   # 地点名称
        "degree": 178.0, # 方位角
        "timestamp": 1545355455,  # gps定位时间
        "altitude": 300, # 高度
        "pacc": 18,   # 定位误差（米）
        "misc": ":18",   # gps调试信息
        "longitude": -289781460,  # 经度
        "location_type": 0, # 0:ROOFTOP; 1:RANGE_INTERPOLATED; 2:GEOMETRIC_CENTER; 3:APPROXIMATE
        "pvt_time": 1545355455, 
        "clongitude": -289781460, # 加密后的经度
        "temp": 12, # 温度
        "begin_time": 1545355455,   # 报文时间
        "latitude": 156384900,  # 纬度
        "name_en": "",  # 位置描述（英文）
        "speed": 0,  # 当前时速（KM/h）
        "id": 20787003,
        "clatitude": 156384900, # 加密后的纬度
        "end_time": 0   # 在redis中获取位置信息数据（如果存在报文时间，以及大于当前数据库中的报文时间， 则将时间设为redis中的报文时间，否则为0）
      },
      "idle_time_switch": 1,   # idle_time信息显示1:启用 0:禁用
      "altitude": 300
      "power_saving": 0 
      "asset": {
        "plate": "", # 车牌号
        "type_id": 2, # assert类型的外键
        "jurisdiction": "sdsds", # 车辆注册地（省或州）
        "vin": "JN8AS5MT8BW173057", # 17 位车架号
        "year": 1, # 车辆生产年份
        "jurisdiction_pid": -1,
        "category": "Light-duty Vehicles", # 分类名称
        "name": "Car One",  # asset名称
        "type_name": "Car", # asset类型名称
        "id": 17,
        "model": "Rogue", # 车辆型号
        "maker": "Nissan" # 车辆制造商
      },
      "charging_status": 0, # 插电状态 0表示未插上，1表示正在充电，2表示充满电
      "latitude": 156384900,
      "fuel_city": 2.0, # 城市油耗量，默认9.0L/100km
      "type": 0,
      "gps": 35,  # GPS信号的SNR值，取值范围0-100
      "update_time": 1545373720,
      "degree": 178.0,
      "timestamp": 1545355455,
      "phone": "",
      "location_is_valid": 1,
      "pbat": 100,  # 设备电池剩余电量百分比，取值范围0-100
      "is_moving": 0,  # 是否移动   1: moving; 0: stop
      "pvt_time": 1545355455, # 报文时间
      "icon": 2, # 终端图标，0：默认； 1：汽车；2：摩托车；3：男人；4：女人; 5: 卡车
      "eco_mode": 0,  # 是否在eco_mode状态
      "exts": {   # 当前车辆安装的外接设备
        "voltage_sensor": [  # 电压传感器
          {
            "code": "gpio0",  # 接线口
            "wire": "Red",  # 接线颜色
            "name": "External Power",  # 传感器名称
            "created_at": 1539328055, # 安装时间
            "updated_at": null,  # 传感器上报数据时间
            "voltage": null   # 数据读数
          }
        ],
        "door_sensor": [ # 门传感器
          {
            "close_alert": 0   # 关门告警
            "code": "gpio4"  # 接线口
            "created_at": 1536158858  # 安装时间
            "name": "Door"  # 传感器名称
            "open": 0      # 传感器读数  默认0
            "open_alert": 0   # 开门告警
            "updated_at": null  # 最近的数据上报时间
            "wire": "White"    # 接线颜色
          }
        ],
        "ruuvi_sensor": [
          {
            "hum": 41.0, # 湿度的读数
            "updated_at": 1545383804,  # 最近一次上报数据的时间
            "temp_upper": 100.0,  # 温度告警上限
            "rssi": 72,
            "id": "C15D487F929C",  # 传感器的mac地址
            "hum_upper": 100.0,  # 湿度告警上限
            "bat": 98,  # 电量读数
            "name": "C15D487F929C",    # 传感器名称
            "temp": 21.6,  # 温度读数
            "created_at": 1534236925,  # 安装时间
            "temp_lower": -40.0,  # 温度告警下限
            "hum_alert": 0,   # 湿度告警开关
            "hum_lower": 0.0,   # 湿度告警下限
            "temp_alert": 0  # 温度告警开关
          }
        ],
        "pto_sensor": [
          {
            "on": 0,  
            "wire": "White",  # 接线颜色
            "name": "PTO",   #传感器名称
            "created_at": 1539228642,   # 安装时间
            "updated_at": 1544596830,   # 最近的一次上报数据的时间
            "off_alert": 0,    
            "code": "gpio4",   # 接线口
            "on_alert": 0
          },
        "temperature_sensor": [ # 温度传感器
          {
            "wire": "Yellow", # 接线颜色
            "name": ";.",    # 传感器名称
            "temp": null,   # 温度读数  
            "created_at": 1529982746,  # 安装时间
            "updated_at": 0,   # 最近的上报数据的时间
            "temp_lower": -40.0,  # 温度触发告警下限值
            "code": "gpio1",   # 接线口
            "temp_upper": 100.0,  # 温度触发告警上限值
            "temp_alert": 0    # 告警开关
          }
        ]
      },
      "name": "",
      "temp": 5,  # 当前tracker的温度
      "eco_mode_hb_hour": 0,  # 在eco_mode 状态的时间
      "longitude": -289781460,
      "alias": "Car One",
      "fuel_switch": 1,
      "sn": "0000031737",
      "is_idle": 0,  # 是否是idle状态
      "pacc": 18.0,
      "login": 1,
      "model": "CH311",  # 终端模型名称
      "gsm": 31  # GSM信号强度
    }
  ]
}
```

### 2. 轨迹播放 trip replay
URL： /api/v1/trip/replay

支持方法： GET

支持客户端： Web,Android,IOS

#### GET方法
功能描述： 获取查询时间范围内的终端轨迹详细信息

**请求参数：**

|参数名称|参数类型|描述|
|-------|:------:|-----------------|
|id|string|终端id|
|start_time|int|查询开始时间|
|end_time|int|查询结束时间|
Example:

```
start_time=1545627600&end_time=1545713999&id=89302720396930726810
```

**返回结果：**

注：所有制量单位采用公制

|参数名称|参数类型|描述|
|-----|:-----:|--------------------|
| segments | array | 行驶轨迹段集合 |
|  | segment - object | start_driving: int 开始行驶时间<br>end_driving: int 结束形式时间<br>driving_time: int 行驶总时间<br>distance: int 行驶总距离<br>pvts: array 行驶轨迹点集合 |
|  | pvt - object | timestamp: int 定位时间<br>address: string 地址名称<br>degree: int 深度<br>altitude: int 海拔<br>speed: int 车速<br>longitude: int 经度<br>latitude: int 纬度 |
| stops | array | 停留点信息集合 |
|  | stop - object | start_stopping: int 开始停留时间<br>end_stopping: int 结束停留时间<br>stopping_time: int 停留总时间<br>timestamp: int 定位时间<br>address: string 地址名称<br>degree: int 深度<br>altitude: int 海拔<br>speed: int 车速<br>longitude: int 经度<br>latitude: int 纬度 |
| alerts | array | 告警信息集合 |
|  | alert - object | timestamp: int 定位时间<br>address: string 地址名称<br>category: int 告警类型<br>degree: int 深度<br>altitude: int 海拔<br>speed: int 车速<br>longitude: int 经度<br>latitude: int 纬度 |
| total | object | stopping_time: int 总计停留时间<br>driving_time: int 合计行驶时间<br>distance: int 合计行驶距离 |
| hash_ | string | 记录查询缓存hash键值 |
Example:
```json
{
  "status": 200,
  "message": "Operation is successful.",
  "data": {
    "hash_": "908a3dac5276ea92c44228d3369041d7",
    "segments": [
      {
        "start_driving": 1545627600,
        "driving_time": 0,
        "end_driving": 1545627600,
        "pvts": [
          {
            "timestamp": 1483087371,
            "address": "",
            "degree": 20,
            "altitude": 20,
            "speed": 22,
            "longitude": 374543064,
            "latitude": 110425608
          }
        ],
        "distance": 0.0
      }
    ],
    "total": {
      "distance": 0.0,
      "driving_time": 0,
      "stopping_time": 6946
    },
    "alerts": [
      {
        "timestamp": 1483089160,
        "address": "96 Russel St, Kitchener, ON N2M 3T7, Canada",
        "category": 11,
        "degree": 20,
        "altitude": 20,
        "speed": 76,
        "pbat": 70,
        "temp": 1,
        "longitude": 374543064,
        "latitude": 110396808
      }
    ],
    "stops": [
      {
        "start_stopping": 1545627600,
        "degree": 0.0,
        "end_stopping": 1545634546,
        "timestamp": 1545627600,
        "latitude": 0,
        "stopping_time": 6946,
        "altitude": 0,
        "address": "",
        "id": -1,
        "longitude": 0
      }
    ]
  }
}
```
### 3. 轨迹时间轴 trip timeline

URL: /api/v1/trip/timeline

支持方法: GET

支持客户端：Web,Android,IOS

####GET方法
功能描述：按日查询终端drive、stop、idle时间详情、轨迹以及告警详细信息 

*请求参数：*

| 参数名称 | 参数类型 | 描述                                 |
|:----------|:--------:|--------------------------------------|
| ids | string | 多个终端ids，并且以","分隔<br/>在url中以"%2C"来代表"," |
| start_time | int | 查询开始时间 |
| end_time | int | 查询结束时间 |
Example:
```http request
start_time=1545627600&end_time=1545713999&ids=89302720396930726810%2C08cf55e12b4646389e519c63704064e7
```

**返回结果：**

注：所有制量单位采用公制

| 参数名称 | 参数类型 | 描述                                 |
|:----------|:--------:|------------------------------------|
| id | string | 终端id |
| alias | string | 终端别名 |
| segments | array | 行驶轨迹段集合 |
|  | segment - object | start_driving: int 开始行驶时间<br>end_driving: int 结束形式时间<br>driving_time: int 行驶总时间<br>distance: int 行驶总距离<br>pvts: array 行驶轨迹点集合 |
|  | pvt - object | timestamp: int 定位时间<br>address: string 地址名称<br>degree: int 深度<br>altitude: int 海拔<br>speed: int 车速<br>longitude: int 经度<br>latitude: int 纬度 |
| stops | array | 停留点信息集合 |
|  | stop - object | start_stopping: int 开始停留时间<br>end_stopping: int 结束停留时间<br>stopping_time: int 停留总时间<br>timestamp: int 定位时间<br>address: string 地址名称<br>degree: int 深度<br>altitude: int 海拔<br>speed: int 车速<br>longitude: int 经度<br>latitude: int 纬度 |
| idles | array | 接电停留信息集合 |
|  | idle - object | start_idle: int 开始接电停留时间<br>end_idle: int 结束借电停留时间<br>idle_time: int 接电停留总时间 |
| alerts | array | 告警信息集合 |
|  | alert - object | timestamp: int 定位时间<br>address: string 地址名称<br>category: int 告警类型<br>degree: int 深度<br>altitude: int 海拔<br>speed: int 车速<br>longitude: int 经度<br>latitude: int 纬度 |
| total | object | stopping_time: int 总计停留时间<br>driving_time: int 合计行驶时间<br>distance: int 合计行驶距离<br>idle_time: int 合计接电停留距离 |
Example：
```json
{
  "status": 200,
  "message": "Operation is successful.",
  "data": [
    {
      "timestamp": 1545454800,
      "segments": [
        {
          "start_driving": 1545454800,
          "driving_time": 0,
          "end_driving": 1545454800,
          "pvts": [
            {
              "timestamp": 1483087371,
              "address": "",
              "degree": 20,
              "altitude": 20,
              "speed": 22,
              "longitude": 374543064,
              "latitude": 110425608
            },
            {
              "...": "..."
            }
          ],
          "distance": 0.0
        },{
          "...": "..."
        }
      ],
      "alerts": [
        {
          "timestamp": 1483089160,
          "address": "96 Russel St, Kitchener, ON N2M 3T7, Canada",
          "category": 11,
          "degree": 20,
          "altitude": 20,
          "speed": 76,
          "pbat": 70,
          "temp": 1,
          "longitude": 374543064,
          "latitude": 110396808
        },{
          "...": "..."
        }
      ],
      "stops": [
        {
          "start_stopping": 1545454800,
          "degree": 0.0,
          "end_stopping": 1545541199,
          "timestamp": 1545454800,
          "latitude": 0,
          "stopping_time": 86399,
          "altitude": 0,
          "address": "",
          "id": -1,
          "longitude": 0
        },{
          "...": "..."
        }
      ],
      "alias": "All Sensors",
      "idles": [
        {
          "start_idle": 1483087371,
          "end_idle": 1483087371,
          "idle_time": 80
        },{
          "...": "..."
        }
      ],
      "total": {
        "distance": 0.0,
        "driving_time": 0,
        "idle_time": 0,
        "engine_time": 0,
        "stopping_time": 86399
      },
      "id": "89302720396930726810"
    },{
      "...": "..."
    }
  ]
}
```

### 4. 用户资料 user profile
支持方法： PUT

支持客户端：Web,Android,IOS

####PUT方法
功能描述： 修改当前用户的资料

请求参数：

|参数名称|参数类型|描述|
|:-----:|:-------:|---------|
|last_name|string |姓|
|first_name|string |名|
|title|string |称呼|
|actions|array|可执行的操作|
|timezone_city|string|时区城市|
|id|string|user表uid|
|city|string|所属城市|
|address|string|地址2|
|billing_email|string|绑定的Email|
|units|int|制量单位:0:公制单位；1：英制单位|
|email|string|邮箱|
|plan_limits|array|告警通知类型限制|
| |plan_limits-object|alert_email: int 邮件通知<br/>alert_app: int app通知<br/>alert_sms: int 短信通知<br/>alert_voice: int 语音通知|
|province|string|所属省份ID|
|company|string|所属公司|
|time_format|int|时间格式 0为12小时制 1为24小时制|
|country|string|所属国家ID|
|avatar|string|用户头像|

Example:
```python
{
  "last_name": "Zhang",
  "actions": [
    "label",
    "trip_replay",
    "timeline",
    "reports",
    "pg_visit",
    "maintenance",
    "state_mileage",
    "notifications",
    "tracker_settings",
    "geo",
    "poi"
  ],
  "timezone_city": "America/Toronto",
  "id": "rzhang@cloudhawk.com",
  "city": "Waterloo",
  "first_name": "Johnson",
  "address2": "cba",
  "title": "Mr",
  "billing_email": "rzhang@cloudhawk.com;test11@google.com;test10@google.com",
  "units": 0,
  "email": "cloudhawkadmin@rongrongzhang.com",
  "plan_limits": {
    "alert_email": 1,
    "alert_app": 1,
    "alert_sms": 1,
    "alert_voice": 1
  },
  "province": 9,
  "company": "DBJTech Zhuhai",
  "time_format": 0,
  "phone": "1-(4242) 53453-5345",
  "is_admin": 1,
  "address": "abc",
  "postalcode": "N2V 2C3",
  "date_format": 0,
  "country": 124,
  "first_login": 0,
  "avatar": "https://s3.amazonaws.com/ch-static-beta/avatar/user/7d336492027511e9911b0e00d85059811545103924.png?t=1545634468334",
  "$meta": {
    "status": 200,
    "message": "Operation is successful."
  }
}
```

**返回结果：**

Example
```json
{"status": 200, "message": "Operation is successful."}
```
### 5. 修改用户密码 change password
URL：/api/v1/password

支持方法: PUT

支持客户端：Web,Android,IOS

**PUT方法：**

功能描述： 修改当前用户的登陆密码

请求参数:

|参数名称|参数类型|描述|
|-----|:-----:|--------|
|old_password|string |旧密码|
|password|string|新密码|
Example：
```json
{
  "old_password": "111111",
  "password": "123456"
}
```

返回结果：
Example：
```json
{"status": 200, "message": "Operation is successful."}
```

## 6. 退出登录
URL：/api/v1/logout 

支持方法: GET

支持客户端：Web,Android,IOS

**GET方法：**

功能描述： 用户退出当前的登陆状态

请求参数：

无

返回结果：
Example：
```json
{"status": 200, "message": "Operation is successful."}
```
