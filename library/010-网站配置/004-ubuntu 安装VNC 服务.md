http://community.bwbot.org/topic/191/ubuntu-%E5%AE%89%E8%A3%85vnc-%E6%9C%8D%E5%8A%A1

ubuntu ��װVNC ����

 
����Ubuntu��ʱ�򾭳���ҪԶ���������ӣ���õ��������VNC��VNC��һ�����ŵ�Э�飬ʵ�ֵĿͻ����кܶࡣ���ǱȽϸ���ʵ��֮��Ŀǰ��õľ���x11vnc��������򲻽����շѣ��ǿ�Դ�ģ����һ�֧��opengl���򡣱���rviz֮��ĳ���Ҳ�����������ˡ�

�������һ�°�װ��������������Ubuntu 14.04Ϊ���ӣ������16.04���Ժ�汾Ҫ�����������ļ�Ҫ����Ӧ�޸ġ�

��װx11vnc

sudo apt-get install x11vnc -y

���÷�������

sudo x11vnc -storepasswd /etc/x11vnc.pass 

���������ļ�

��/etc/init �´���һ��x11vnc.conf���ļ����ļ���������

description "xiaoqiang vnc server"

start on runlevel [2345]

stop on runlevel [06]

script

    exec /usr/bin/x11vnc -auth guess -capslock -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared

end script

��������

sudo service x11vnc start

���ʷ���

����һ��vnc�ͻ���,�������������

https://www.realvnc.com/en/connect/download/viewer/

�򿪿ͻ���

����Ŀ��IP�����Ӻ��������룬֮��Ϳ������������ˡ�

����16.04�汾�͸��°汾��Ubuntu�����԰�������ļ��ķ�����������

https://github.com/longhr/ubuntu1604hub/blob/master/ubuntu1604VNC.sh

ע�ⰲװ���֮���ڲ�����ʾ��ʹ��rvizʱ���ǻᱨ����ʱ�����hdmiתvga��ת��ͷ��������ʾ����ֻ��ת��ͷ���Ϳ��Դ�����ʹ���ˡ������Ҫ�����ֱ��ʿ����������������÷ֱ���һ����������������е���