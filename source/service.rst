adg服务管理文档
===============
服务管理原型设计、服务对象管理

原型设计
----------------
 服务管理主要对应L4和L7两个网络层：

	* ``L4：tcp udp htpp``
	* ``L7: tcp http ssl https``

 服务可以没有名称，在服务均衡中要用到服务配置（链路+服务）可以快速添加服务。在涉及到的L7层的服务时要加密，需要上传加密证书（enceryptionCertificate），并且选择加密证书的版本。如果是L4层的下面的上传证书字段不显示。

.. image:: http://pic.yupoo.com/fuluoxinchen/Cs6FGHZ2/medish.jpg

服务对象管理
--------------

#. 数据库字段设计

 **YML格式定义** ::

	id:                     ~ 
	serviceName:            {type:varchar(255)}
	protocol:               {type:varchar(255), required: true}
	port:                   {type:integer, required: true}
	encrCertificate: 	{type:varchar(255)}
	protocolVersion:        {type:varchar(255)}
	clientAuthentic:        {type:boolean}

#. 固定的字段

 ADG内置了一些常见的服务，这些服务有


 =========  =====  ======  ===========
 NAME       TYPE   PORT    DESCRIPTION
 =========  =====  ======  ===========
 http       HTTP   80 	
 https      HTTPS  443	
 dns        UDP	   53
 msts       MSTS   3390	
 mysql      TCP			
 sqlserver  TCP		
 =========  =====  ======  ===========

 **系统内置服务不可被删除，也不可以被编辑**

#. 编码

 service表内的数据进行相关的操作，包括添加、删除
