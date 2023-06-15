# EdgeAI-ImageClassification
**Device:** [Jetson Nano Developer Tool Kit 2GB](https://developer.nvidia.com/embedded/jetson-nano-developer-kit) <br>
**Sites:** [Nvidia DLI](https://courses.nvidia.com/courses/course-v1:DLI+S-RX-02+V2/) <br>
**References:** [Getting Started with AI on Jetson Nano](https://ithelp.ithome.com.tw/articles/10297084) <br>
**Description:** With Using _JetsonNano_ to train and classify specific condition. <br>

## Processing 
1. Install sorresponding suites: <br>
   ```
   sudo apt-get install nvidia-container-toolkit nvidia-container-runtime nvidia-container-csv-*
   ```
2. Reinstall designated version **docker**: <br>
   ```
   1. wget https://launchpad.net/ubuntu/+source/docker.io/20.10.2-0ubuntu1~18.04.2/+build/21335731/+files/docker.io_20.10.2-0ubuntu1~18.04.2_arm64.deb
   2. sudo dpkg -i docker.io_20.10.2-0ubuntu1~18.04.2_arm64.deb
   3. rm docker.io_20.10.2-0ubuntu1~18.04.2_arm64.deb
   4. sudo apt-get install containerd
   ```
3. Build **package** corresponding version text: <br>
   ```
   sudo gedit /etc/apt/preferences
   ```
4. Using _Text Editor_ to edit: <br>
   ```
   Package: docker.io
   Pin: version 20.10.2*
   Pin-Priority: 1001
   Package: containerd
   Pin: version 1.5.2*
   Pin-Priority: 1001
   ```
5. Reboot System: <br>
   ```
   sudo reboot
   ```
6. Build directory: <br>
   ```
   mkdir -p ~/nvdli-data
   ``` 
7. Activate **docker**: <br>
   ```
   sudo docker run --runtime nvidia -it --rm --network host \
     --volume ~/nvdli-data:/nvdli-nano/data \
     --device /dev/video0 \
     nvcr.io/nvidia/dli/dli-nano-ai:v2.0.1-r32.6.1tw
   ```
8. Click into **classification_interactive.ipynb** and start your adventure! <br>
