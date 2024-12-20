## python相关学习
### Subprocess模块
作用：允许生成新的进程执行命令行指令
```shell
subprocess.run(args, *, stdin=None, input=None, stdout=None, stderr=None, capture_output=False, shell=False, cwd=None, timeout=None, check=False, encoding=None, text=None, env=None)
```
返回值：subprocess.CompletedProcess
主要参数：
args：表示要执行的命令。必须是以字符串为元素的 list or tuple 。
stdin、stdout 、stderr：进程的标准输入、输出和错误。
<font color=Blue>
{可取值：
subprocess.PIPE,      #subprocess.PIPE 表示为子进程创建新的管道
subprocess.DEVNULL,   #subprocess.DEVNULL 表示使用 os.devnull
一个已经存在的文件描述符, 
已经打开的文件对象,
None                  #默认使用的是 None，表示什么都不做。
}
</font>
encoding: 如果指定了该参数，则 stdin、stdout 和 stderr 可以接收字符串数据，并以该编码方式编码。否则只接收 bytes 类型的数据。
shell：如果该参数为 True，将通过操作系统的 shell 执行指定的命令。
check: 如check=true, 当进程退出码为非0时，将生成 CalledProcessError 异常

使用python脚本在终端执行 <fron color=Blue>yolo predict model=yolo11n.pt source='cat.jpg'</font>
```python
import subprocess

def run_yolo_predict(model, source):
    command = f"yolo predict model={model} source={source}"
    process = subprocess.run(command, shell=True, check=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
    print(process.stdout.decode())
    if process.returncode != 0:
        print(process.stderr.decode())

if __name__ == "__main__":
    model_path = r"/root/yolo/yolo11n.pt"  
    image_path = r"/root/yolo/cat.png"    

    run_yolo_predict(model_path, image_path)
```
