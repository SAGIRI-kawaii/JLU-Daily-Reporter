# JLU Daily Reporter



本项目基于TechCiel/jlu-health-reporter[链接](https://github.com/TechCiel/jlu-health-reporter)进行少量修改

为吉林大学本科生每日打卡所作的自动机器人。（三测温一点名版）

以 WTFPL 授权开源。

## 免责声明

本自动程序为个人使用开发，未经充分测试，不保证正常工作。

本自动程序适用于 2020-2021 秋季学期吉林大学本科生每日健康打卡（三测温一点名），不保证按时更新。研究生打卡是否适用未经测试。

**使用本程序自动提交打卡，你必须实际完成一日三测温，在指定时间回到寝室，并在身体状况出现异常时立刻联系校医院和辅导员。**

__**如运行本程序，您理解并认可，本自动程序的一切操作均视为您本人进行、或由您授权的操作。本程序作者对您因使用此程序可能受到的损失、处罚以及造成的法律后果不负任何责任。**__

## 使用说明

需要 Python 3 ，先 `pip3 install requests` 。

运行之前**先登录平台提交一次打卡**，务必确保信息准确。

参照 example-config.json 建立配置文件 config.json ，填入登录信息和对应表单项的值（注意均使用字符串值）。

**请一定要正确配置config文件，因为没有正确配置造成的一切后果与程序作者无关**

目前尚未适配校外居住 请见谅

```json
{
	"transacation": "BKSMRDK",
	"users": [
		{
			"username": "zhangsan2120",
			"password": "password",
			"fields": {
				
				"fieldSQxq": "1",//校区号（要填写的内容请自行f12查找不详细写了
				"fieldSQgyl": "1",//公寓号
				"fieldSQqsh": "1088"//寝室号
			}
		},
		{
			"username": "lisi2120",
			"password": "password",
			"fields": {
				"fieldSQxq": "1",
				"fieldSQgyl": "1",
				"fieldSQqsh": "1088"
			}
		}
	]
}

```



Crontab 模式：

```
5 7,11,17,21 * * * /usr/bin/python3 /path/to/jlu-daily-reporter.py >> reporter.log 2>&1
# 5分开始避免服务器时间略有偏差导致失败
```

手动模式（请在时段内启动）：

```
./jlu-daily-reporter.py
```

## 免责声明

期末结束后可能会写一个web端自动生成json

**敬请期待**

## 联系

欢迎开 issue / pr ，随缘处理。
