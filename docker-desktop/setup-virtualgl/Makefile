all:
	nvidia-docker build -t plumbee/nvidia-virtualgl .

run:
	xhost +local:root
	nvidia-docker run \
				 --privileged \
				 -ti \
		     --env="DISPLAY" \
				 --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
				 --volume="/usr/lib/x86_64-linux-gnu/libXv.so.1:/usr/lib/x86_64-linux-gnu/libXv.so.1" \
				 plumbee/nvidia-virtualgl:latest #vglrun glxgears
	#xhost -local:root # resetting permissions

clean:
	nvidia-docker system prune -a
