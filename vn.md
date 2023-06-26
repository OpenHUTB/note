


Visual Navigation
No module named 'h5py'
pip install h5py  (和matlab调用python冲突)
*******************

glxinfo | grep -i direct
glxgears   显示齿轮

SSE2，全名为Streaming SIMD Extensions 2


安装Bazel

sudo apt-get install openjdk-8-jdk

echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -

sudo apt-get update && sudo apt-get install bazel

sudo apt-get install realpath
sudo apt-get install libsdl2-dev


bazel run :python_random_agent --define graphics=sdl -- \
               --length=10000 --width=640 --height=480

bazel run :game -- --level_script=tests/empty_room_test --level_setting=logToStdErr=true