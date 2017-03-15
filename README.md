# tensorflow-automated-training
Dockerfile to easily deploy tensorflow training w/o kubernetes.

Clone this repo. Build bazel, tensorflow-1.0.0-cp27-cp27mu-linux_ppc64le.whl using automated build uploaded as github project. Place them here. Modify the docker file if those two binaries have different names.

# build the docker image
```bash
docker build -f Dockerfile_ML_train -t trainer .
```

It is assumed that cuda 8.0 is installed on your host on /usr/local/cuda-8.0/ and /usr/lib/powerpc64le-linux-gnu/, nvidia-375 driver is installed on your host on /usr/lib/nvidia-375/, cudnn library is properly extracted in /usr/local/cuda-8.0/ and you want your output of trained model in /root/container-trained/
# run the docker image
```bash
docker run -it --privileged -v /usr/local/cuda-8.0/:/usr/local/cuda-8.0/ -v /usr/lib/powerpc64le-linux-gnu/:/usr/lib/powerpc64le-linux-gnu/ -v /usr/lib/nvidia-375/:/usr/lib/nvidia-375/ -v /root/container-trained/:/flowers_train trainer /bin/bash -c "./run-trainer.sh"
```
