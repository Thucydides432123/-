火灾检测系统软件说明书

概述
火灾检测系统是一个基于YOLOv11模型的火焰和烟雾识别工具，旨在通过图像和视频流实现快速准确的火灾检测。

系统要求
Python 3.6 或更高版本
OpenCV 4.x
Flask
访问互联网以下载依赖项

安装依赖
在命令行中运行以下命令以安装所需的依赖项：
```bash
pip install -r requirements.txt
```

配置
- 数据集路径：编辑 `mycoco.yaml` 文件，设置正确的数据集路径。
- 模型权重：确保 `train.py` 脚本中指定的模型权重文件路径正确。

运行
1. 训练模型：运行 `train.py` 脚本开始模型训练。
   ```bash
   python train.py
   ```
2. 启动应用：运行 `app.py` 启动 Flask 应用。
   ```bash
   python app.py
   ```

使用指南
访问 `http://127.0.0.1:3389` 在浏览器中查看用户界面。使用界面上传图片或视频，点击相应的按钮进行火灾检测。对于实时摄像头检测，选择“电脑摄像头实时识别”或“外接摄像头实时识别”并启动摄像头。

问题解决
- 摄像头无法启动：检查摄像头连接，确保没有其他应用正在使用摄像头。
- 检测不准确：可能需要调整YOLO模型的置信度阈值或进行更多的数据训练。
- 应用无法启动：检查Flask服务器日志，确保所有依赖都已正确安装。

贡献指南
欢迎为火灾检测系统贡献代码或提供反馈。请提交拉取请求或创建问题以报告错误或提出改进建议。

文件结构
```
fire_detection_system/
│
├── app.py            # Flask 应用入口
│
├── train.py          # 模型训练脚本
│
├── mycoco.yaml      # 数据集配置文件
│
├── requirements.txt  # 项目依赖
│
├── dataset        # 数据集存放位置
│   ├── train       # 训练数据集
│   ├── val        # 验证数据集
│   └── test        # 测试数据集
│
├── runs           # 训练结果存放位置
│   ├── exp        # 训练过程中的实验结果
│   └── last        # 最后一次训练的结果
│
├── static         # 用户界面背景图片存放位置
│   └── bg.jpg      # 背景图片文件
│
├── templates     # 网页模板存放位置
│   └── index.html    # 主页面模板
│
```

请按照以上结构组织您的项目文件，并根据需要调整路径和配置。

详细说明

1. app.py：这是启动整个应用的入口点。它使用了Flask框架来搭建后端服务，处理前端的请求，包括图片和视频的上传、处理以及摄像头的实时检测。

2. train.py：这个脚本用于训练YOLO模型。它加载数据集，配置训练参数，然后开始训练过程。训练完成后，模型的权重会被保存，用于后续的检测任务。

3. mycoco.yaml：这是一个配置文件，用于指定数据集的路径、类别名称等信息。在开始训练之前，用户需要根据自己数据集的实际情况修改这个文件。

4. requirements.txt：这个文件列出了项目依赖的所有Python库。用户需要运行 `pip install -r requirements.txt` 命令来安装这些依赖。

5. dataset 文件夹：这个文件夹包含了用于训练、验证和测试模型的数据集。用户需要将自己的火焰和烟雾图片放入这个文件夹中，并确保 `mycoco.yaml` 文件中的路径与之匹配。

6. runs 文件夹：这个文件夹用于存放模型训练过程中的实验结果，包括权重文件和训练日志。

7. static 文件夹：用于存放静态文件，如背景图片。在 `index.html` 中引用的背景图片就放在这个文件夹中。

8. templates 文件夹：存放Flask的HTML模板文件。`index.html` 是主页面，用户通过浏览器访问的就是这个页面。

通过以上详细说明，用户应该能够清楚地了解火灾检测系统的各个组成部分以及如何使用它们。





用户使用说明书
1. 概述
欢迎使用火灾检测系统。本系统利用先进的YOLOv11模型，通过用户友好的网页界面，实现对火焰和烟雾的快速识别与定位。本说明书将指导您如何使用本系统。

2. 系统要求
浏览器：支持HTML5和CSS3的现代浏览器。
服务器：能够运行Python和Flask的服务器环境。

3. 启动系统
1. 打开命令行界面。
2. 导航至 `app.py` 文件所在目录。
3. 运行命令 `python app.py` 启动Flask服务器。
4. 访问 `http://127.0.0.1:5000` 在浏览器中查看用户界面。

4. 用户界面介绍
系统界面由以下主要部分组成：
主页：展示系统功能，包括图片火焰识别、视频火焰识别、电脑摄像头实时识别和外接摄像头实时识别。
图片火焰识别：允许用户上传图片文件，系统将识别并标记出火焰和烟雾区域。
视频火焰识别：允许用户上传视频文件，系统将逐帧识别并标记出火焰和烟雾。
实时摄像头识别：提供实时视频流，用户可选择电脑或外接摄像头，系统将实时识别并标记火焰和烟雾。
5. 使用步骤
5.1. 图片火焰识别
1. 在主页点击“图片火焰识别”按钮。
2. 在图片火焰识别页面，点击“开始上传”按钮，选择并上传图片文件。
3. 系统处理后，将在页面上显示原图和标记后的图片。
5.2. 视频火焰识别
1. 在主页点击“视频火焰识别”按钮。
2. 在视频火焰识别页面，点击“开始上传”按钮，选择并上传视频文件。
3. 系统处理后，将在页面上显示原视频和标记后的视频。
5.3. 实时摄像头识别
1. 在主页选择“电脑摄像头实时识别”或“外接摄像头实时识别”。
2. 点击“启动摄像头”按钮，开始实时视频流。
3. 系统将在实时视频流上标记火焰和烟雾。
4. 点击“停止摄像头”按钮，结束实时视频流。
5.4. 返回主页
在任何操作完成后，点击“返回”按钮，返回主页面。

6. 注意事项
确保上传的图片和视频质量良好，以便模型能够准确检测。
在使用实时摄像头功能时，确保摄像头已正确连接并被系统识别。
系统性能可能受到服务器硬件配置和网络条件的影响。

通过遵循本说明书，用户应能顺利操作火灾检测系统，实现火焰和烟雾的有效识别。






