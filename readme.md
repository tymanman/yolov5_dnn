## Fisrst Commit
### [optional]基于opencv4.5环境的编译命令([docker环境镜像地址](https://hub.docker.com/repository/docker/tymanman/yolov5_dnn))
`g++ `pkg-config --cflags opencv4` main.cpp `pkg-config --libs opencv4` -Wl,-rpath=libs -o main`

### 运行命令
`./main img1 img2...`

## Second Commit(2022.4.1)
### [optional]将模型文件编入可执行文件([docker环境镜像地址](https://hub.docker.com/repository/docker/tymanman/yolov5_dnn_2))
执行以下命令生成模型文件的目标文件：
`objcopy -I binary -O elf64-x86-64 -B i386 weights/yolov5m.onnx weights/model.o`

执行以下命令生成脱离库依赖的可执行文件：
`g++ -g -static -I /root/lili_opencv/include/opencv4 -I /usr/include main_full.cpp model.o  -L /root/lili_opencv/lib/ -L /root/lili_opencv/lib/opencv4/3rdparty/ -l:libopencv_dnn.a -l:libopencv_imgcodecs.a -l:libopencv_imgproc.a -l:libopencv_core.a -l:liblibopenjp2.a -l:liblibpng.a -l:liblibtiff.a -l:liblibwebp.a -l:liblibprotobuf.a  -l:libippiw.a -l:libippicv.a -l:libIlmImf.a -l:liblibjpeg-turbo.a -l:libittnotify.a -l:libzlib.a -ldl -lpthread -lstdc++ -l:libc.a  -o main_full_static`

### 运行命令 [模型链接](https://drive.google.com/file/d/1i6_B3Y3qzqZrT9YxPnDF_paBmt4zwDij/view?usp=sharing)
`./main_full_static img1 img2...`
