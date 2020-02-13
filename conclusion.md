# Edge Computing Vision and Challenges 	2016	《IEEE INTERNET OF THINGS JOURNAL》
* 比较重要的一点就是说明了边缘计算的概念：从边缘到云的任意点的计算。
* 明确了和雾计算的区别：雾计算偏向基础设施，边缘计除了基础设施，也有边缘设备及边缘设备的管理


# 边缘计算_万物互联时代新型计算模型_施巍松	2017	《计算机研究与发展》
Edge Computing Vision and Challenges的中文版，内容基本一致


# 边缘计算_现状与展望_施巍松	2019	《计算机研究与发展》
* 点出了支持边缘计算的7个核心技术
	* 网络
	* 隔离技术（**容器化**）
	* 体系结构
	* 边缘操作系统（**ROS机器人操作系统，可能会是边缘计算场景的典型操作系统**）
	* 算法执行框架
	* 数据处理平台
	* 安全和隐私
* 指出边缘计算典型应用
	* 公众安全中实时数据处理（滴滴出行SafeShareRide，可通过边缘设备对车上语音和视频进行处理；消防员身上的设备作为边缘设备，采集火场情况）
	* 智能网联车和自动驾驶
	* 虚拟现实（VR & AR, 将图片渲染等计算任务卸载到边缘服务器）
	* 工业互联网
	* 智能家居（涉及敏感数据，这部分隐私很重要）
	* 智慧城市
* 边缘计算面临的紧迫问题
	* 编程模型（EveryLite，轻量级编程语言，用于边缘计算场景中的微任务）
	* 软硬件选型（基于英伟达GPU的边缘硬件产品，软件上如Tensorflow、Caffe等深度学习框架）
	* 基准程序和标准（用于测试边缘产品性能）
	* 动态调度


# Computation OfﬂoadingToward Edge Computing	2019	《PROCEEDINGS OF THE IEEE》
* computation offloading在云计算时代指的是将计算任务集中于云；而在边缘计算中是指将计算任务分布到靠近边缘的节点上
* Overview of computation offloading
	* Architecture 边缘计算的三层架构(computation offloading所处的架构)：
		* Data Centers (DCs || Cloud)
		* Edge Nodes (Edge infrastructure || Fog)
		* Edge Devices	(User equipment, mobile phone, vehicles, cameras)
	* Simple Analysis of offloading
		* T_local > T_offloading = T_comm + T_remote (本地计算消耗**时间** 与 offloading计算消耗时间)
		* E_local > E_comm	(本地计算消耗**能量** 与 offloading计算消耗能量-即节点将计算任务offloading所消耗的传输能量)
	* Granularity of Offloading
		* Full Offloading(thin-client，客户端只保留display和ui，计算任务都offloading)
		* task/component(将计算任务划分，比如AR的计算任务可划分为1.物体识别2.渲染，可单独将物体识别offloading则为task/component,若1.2都offloading,则为full offloading)
		* method/thread(相比task/component更加细粒度的计算任务划分)
	* Impact of Network Connectivity
		* 结论是wifi比3G和4G有更快offloading的速度，应该是指传播更快，同时wifi更加节省能量，**但是5G的情况没有讨论，这或许可以做一个论文**
* Challenges for Computation Offloading in Edge Computation
	* Application Partitioning - 分为MCC的application partitioning和MEC的application partitioning。其中MCC已经有一些现成的解决方案了，而paper中指出MEC面临的两大挑战有partitioning for multinode offloading和partitioning granularity（包括method,thread,class level等）。
	* Task Allocation
		1. Cloudlet Discovery
			* 根据network-intensive,compute-intensive和avaliable resources去选择合适的cloudlet
			* couldset应该部署在哪里可以达到用户最小的平均时延
		2. Task Scheduling With Resource Management
			* Multiuser,multinode scheduling
			* Dynamic resource management
		3. Task Execution
			* 异构平台（heterogeneous platforms）引出了container和unikernel。
			* serverless computing
* Application Scenarios
	* Vedio Analytics
	* Smart Things (IOT)
	* Intelligent Vehicle Applications
	* Cloud Gaming (云游戏，不在本地而在边缘节点或者云上进行渲染和计算，可以在一定程度上不限设备)
	* Summary
		* 利用边缘节点（而不是云）去进行一些计算任务，可以显著的降低延迟及减小带宽
		* 多层的云和边缘的结构是必要的
		* 边缘服务器在不同的应用程序中有不同的形式，比如在视频分析中为cloudlet；IOT中为IOT hubs；自动驾驶中为bash stations。作者总结->任何可以在靠近数据源的地方进行计算的设备都可以成为边缘节点或边缘基础设施（edge infrastructure）