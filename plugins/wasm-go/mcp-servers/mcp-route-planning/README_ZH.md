# 路径规划

API认证需要的APP Code请在阿里云API市场申请: https://market.aliyun.com/apimarket/detail/cmapi00065113

## 什么是云市场API MCP服务

阿里云云市场是生态伙伴的交易服务平台，我们致力于为合作伙伴提供覆盖上云、商业化和售卖的全链路服务，帮助客户高效获取、部署和管理优质生态产品。云市场的API服务涵盖以下几个类目：应用开发、身份验证与金融、车辆交通与物流、企业服务、短信与运营商、AI应用与OCR、生活服务。
云市场API依托Higress提供MCP服务，您只需在云市场完成订阅并获取AppCode，通过Higress MCP Server进行配置，即可无缝集成云市场API服务。

## 如何在使用云市场API MCP服务

1. 进入API详情页，订阅该API。您可以优先使用免费试用。
2. 前往云市场用户控制台，使用阿里云账号登陆后查看已订阅API服务的AppCode，并配置到Higress MCP Server的配置中。注意：在阿里云市场订阅API服务后，您将获得AppCode。对于您订阅的所有API服务，此AppCode是相同的，您只需使用这一个AppCode即可访问所有已订阅的API服务。
3. 云市场用户控制台会实时展示已订阅的预付费API服务的可用额度，如您免费试用额度已用完，您可以选择重新订阅。

# MCP服务器功能简介文档

## 功能简介
MCP服务器提供了一套全面的路径规划解决方案，支持包括公交、步行、自行车骑行、电动车骑行、驾车等多种出行方式的路线规划，并且还提供了行程距离测量的功能。这些服务旨在帮助用户根据不同的需求和偏好选择最合适的出行方案，从而提高出行效率并节省时间。此外，MCP服务器还考虑到了实际交通状况和个人偏好设置等因素，以确保提供的路线是最优解。

## 工具简介

### 公交路线规划
- **用途**：基于用户的起始点与目的地信息，计算出一条或多条合理的公交车乘车路线。
- **使用场景**：适用于需要乘坐公交车出行的乘客，特别是当用户不熟悉当地公交线路或希望找到最快捷经济的乘车方案时。
- **参数说明**：
  - `alternativeRoute`：返回不同数量的路线选项。
  - `date` 和 `time`：指定查询的具体日期时间和时刻。
  - `destCityCode`, `origCityCode`：分别指定了目的地城市代码及出发地城市代码。
  - `destination`, `origin`：分别是目的地和出发地的经纬度坐标。
  - `maxTrans`：限制了最大换乘次数。
  - 更多参数允许进一步定制化查询条件，例如是否考虑夜班车(`nightFlag`)、特定策略(`strategy`)等。

### 步行路线规划
- **用途**：为用户提供从一个地点到另一个地点的最佳步行路线。
- **使用场景**：适合短途旅行或者在不适合开车的情况下使用。
- **主要参数**：
  - `alternativeRoute`：可选参数，用于获取多条备选路线。
  - `destination` 和 `origin`：必填项，定义了旅程的起点和终点位置。
  - `showFields`：控制返回结果中包含哪些字段。

### 电动车/自行车骑行路线规划
- **用途**：针对电动自行车或普通自行车骑行者设计，提供优化后的骑行路线建议。
- **适用情况**：特别适合于日常通勤或休闲骑行活动。
- **配置选项**：与步行路线规划类似，也支持设定多个备选路线(`alternativeRoute`)以及其他个性化设置。

### 行程距离测量
- **目的**：用来估算两个地理位置之间的直线距离或按照特定交通方式进行的距离。
- **应用场景**：对于需要了解两地间大致距离的用户非常有用。
- **关键参数**：`type` 参数决定了计算方法是直接距离还是基于某种交通工具的实际行驶距离。

### 驾车路线规划
- **功能描述**：给定出发点和目的地后，系统会综合考虑当前路况、限行规定等因素来推荐最佳驾驶路线。
- **目标群体**：面向私家车主或职业司机，尤其是那些经常需要长途驾驶的人士。
- **重要特性**：支持设置避让区域(`avoidpolygons`)、特殊车辆类型(`carType`)以及不同的驾驶策略(`strategy`)等高级选项。

以上即为MCP服务器所支持的各项服务的基本介绍。每种工具都拥有其独特的应用领域，并可通过调整相应参数来满足更加具体的需求。
