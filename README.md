钉钉官方并未提供nodejs包,第一次调用接口的时候非常费事,而且尝试去寻找相关的钉钉考勤数据模块的时候只找到了一些消息啊,只能办公啊,免登啊之类的模块,有关考勤数据的似乎没有
[关于dd的npm包中一个有较全面](https://www.npmjs.com/package/egg-dd-sdk),但是这个包似乎是egg的模块,我没有尝试单独使用

不得不说钉钉小程序的服务端api真的恶心,为了获得考勤数据要拿access_tonken然后再拿员工id列表,然后再拿员工id列表对应的员工姓名和部门,然后才能拿员工考勤数据,这个考勤数据还有限制,不能查询半年以前的,一次获取的结果还有限制,真的让人很无语,
## 使用方法
**需要拿考勤信息的人请注意**因为拿下来的数据要放到内存当中处理,所以这个脚手架需要一点启动时间(100人大概3秒左右)才能拿到数据,3秒后随便调用考勤信息
如果仅仅是需要获取用户/部门信息,发送工作消息,则不需要准备时间(但是这这包会自动准备到用户id/姓名部门的对应表阶段,)


安装

> npm install ddinit


构建并使用,后三位选填,不填的话不会缓存周/月考勤数据,最后一位是每日考勤数据的更新速度,单位是毫秒
```javascript
  import DDdata from 'ddinit'
  const dd =  new DDdata('这里换成你的appkey', '这里换成你的appsecret', 4, 2, 500)
```

[详细使用可以参照这里的示例](https://github.com/TCmoshuying/dd-cli)