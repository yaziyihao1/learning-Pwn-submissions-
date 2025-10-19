解题wp

题目1(test)

先启动靶机，nc +ip+端口，连接到靶机，再用ls显示其目录，在目录中直接找到“flag”,用cat flag 读取flag里的‘flag’，得到flag{5e72edcd-1e99-4a5d-816c-b88b72b0306b}，返回平台，输入flag，正确！

<img width="361" height="447" alt="image" src="https://github.com/user-attachments/assets/57326237-3104-4c3f-8391-a291c7ec9cd7" />

学习：nc访问，ip，端口

题目2(pwn's door)

1.启动靶机，下载文件，nc访问靶机，发现要一个密码打开'door',要寻找密码，输错后提示用IDA解决，
2.导入door到IDA前，先判断*86还是*64格式，重起一个指令框，checksec door,找到door的格式是amd64
3.在IDA中打开door,选main函数，TAB，打开C格式，发现if ( n7038329 == 7038329 )条件语句，密码是7038329
4.返回密码输入窗口，输入密码7038329，输入cat flag,得到flag:flag{20a95d18-50c0-4288-9637-f26117057ee1}
5.返回平台，输入flag，正确！

阻碍：关于对door的checksec door 报错：
duck@duck-VVP:~$ checksec door
usage: pwn checksec [-h] [--file [elf ...]] [elf ...]
pwn checksec: error: argument elf: can't open 'door': [Errno 2] No such file or directory: 'door'
解决：地址不精确，checksec 桌面/door正确打开【哈哈】

<img width="530" height="376" alt="image" src="https://github.com/user-attachments/assets/f8c66013-a939-4ff7-9a6f-63ac169b942d" />

<img width="990" height="688" alt="image" src="https://github.com/user-attachments/assets/bcc8f862-b521-4031-866c-23e30ff7d6a9" />

<img width="695" height="334" alt="image" src="https://github.com/user-attachments/assets/cc74502f-1ade-4a89-861c-e59d28d7d4e3" />



题目3(INTbug)
1.启动靶机，下载文件，nc访问靶机，输入返回‘You can only input positive number!’输入ls无效，准备IDA
2.判断INTbug为*86or*64格式，另起指令框，精确地址后checksec INTbug,得其为64位
3.IDA打开INTbug，选main函数，TAB，打开C格式，有fuc未知函数，打开fuc,运算逻辑：2字节v1=0与4字节v2=0，循环：输入v2，v2<=0会跳出，当v1自增<0是输出flag，2字节int最大32767，当执行32768次循环后数据溢出得到负值
4.输入32768次v2费时，执行脚本循环执行32768次，编写for循环脚本，运行(python intbug.py)
5,得到flag:flag{8d36bebf-686b-405e-8a4b-662a481dd979},返回平台，输入flag，正确！


<img width="1280" height="673" alt="image" src="https://github.com/user-attachments/assets/f0d91669-e934-47a4-8d89-a2dd6a335f36" />

<img width="1007" height="316" alt="image" src="https://github.com/user-attachments/assets/c3718061-92a0-41b7-a978-fa5c1a9d62e5" />

<img width="753" height="693" alt="image" src="https://github.com/user-attachments/assets/854448e8-16db-46b6-97a9-7a7d57c54fce" />

<img width="753" height="693" alt="image" src="https://github.com/user-attachments/assets/3339d586-026d-465d-9d7a-f401ab8df359" />

<img width="863" height="672" alt="image" src="https://github.com/user-attachments/assets/91eadbe4-e20e-4863-b910-c8b16339472c" />

学习：虚拟机脚本创建：vim (name).py
python3 for循环结构

题目4(ret2text1)
1.检查为64位，丢到IDA
2.尚未完结

<img width="848" height="609" alt="image" src="https://github.com/user-attachments/assets/5a83d532-31b5-46b5-96da-21bec55008fa" />


