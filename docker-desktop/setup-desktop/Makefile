all:
	nvidia-docker build -t ubuntu-desktop .

run: 
	xhost +
	nvidia-docker run \
				--env="DISPLAY" \
				--volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
				--volume="/usr/lib64/libXv.so.1:/usr/lib/x86_64-linux-gnu/libXv.so.1" \
				--privileged \
				--rm \
				-it \
				-p 5901:5901 \
				-p 8888:8888 \
				-p 8088:8088 \
				--net=host \
				-e USER=root \
				ubuntu-desktop \
    bash -c "rm -f /tmp/.X11-unix/X1 && vncserver :1 -geometry 1440x900 && tail -F /root/.vnc/*.log"

#				--volume="/usr/lib/x86_64-linux-gnu/libXv.so.1:/usr/lib/x86_64-linux-gnu/libXv.so.1" \
				-d \
