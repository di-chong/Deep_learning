# 深度学习云端训练

**没必要用自己的电脑去跑深度学习，云端训练就行**

#### *<u>**前置：先在本地测一下能不能跑起来，测一下就行</u>***

#### 1.打开 [https://www.autodl.com](https://www.autodl.com/)



![1763741899755](C:\Users\houliang wang\AppData\Roaming\Typora\typora-user-images\1763741899755.png)



#### 2.进入 **「JupyterLab」** 页面

![1763748223606](C:\Users\houliang wang\AppData\Roaming\Typora\typora-user-images\1763748223606.png)



#### 3.上传-解压-进入终端

```bash
unzip xxx.zip
```

![1763748365381](C:\Users\houliang wang\AppData\Roaming\Typora\typora-user-images\1763748365381.png)

#### 4.在 JupyterLab 里新建 Terminal

##### 4.1.装依赖（AutoDL 自带 cuda，不用你管）

pip install -r code/requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple

##### 4.2.进入代码目录

cd /root/VIT_Project/code

##### 4.3. 运行（把路径指到数据文件夹）,如果希望关闭界面后台运行，就在终端进行命令

```bash
cd /root/VIT_Project/code
nohup python main.py \
  --train_label ../imagedata/train_label.txt \
  --val_label   ../imagedata/validation_label.txt \
  --train_data  ../imagedata/train \
  --val_data    ../imagedata/val \
  -b 32 --lr 0.01 --epochs 50 --print-freq 100 \
  > run.log 2>&1 &
```

  > 

![1763747788638](C:\Users\houliang wang\AppData\Roaming\Typora\typora-user-images\1763747788638.png)

![1763747995849](C:\Users\houliang wang\AppData\Roaming\Typora\typora-user-images\1763747995849.png)

日志观察训练：tail -f run.log

![1763748052038](C:\Users\houliang wang\AppData\Roaming\Typora\typora-user-images\1763748052038.png)

之后就可以退出了，训练完关闭云端实例即可