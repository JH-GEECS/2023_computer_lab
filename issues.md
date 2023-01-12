# lab1
1. 우분투 설치 시에 화면 짤리면 alt+f7 누르고 화면 옮기기
2. ubuntu1 / ubuntu1
3. ip 초기 설정
	172.29.0.88, 255.255.255.0, 172.29.0.254
	203.237.32.100
3. vi 초기에 이상할 때
	1. sudo apt-get install vim
4. ubuntu 20.04.4 release link 손상
	1. http://old-releases.ubuntu.com/releases/focal/ubuntu-20.04.4-live-server-amd64.iso 로 사용
5. 가상화 문제 해결
	1. sudo kvm -m 1024 -name tt -smp cpus=2,maxcpus=2 -device virtio-net-pci,netdev=net0 -netdev tap,id=net0,ifname=vport_vFunction,script=no -boot d vFunction20.img -cdrom ubuntu-20.04.4-live-server-amd64.iso -vnc :5 -daemonize -monitor telnet:127.0.0.1:3010,server,nowait,ipv4 -cpu host
		1. svm은 amd 기술인데, vmx를 사용하기 위해
6. 172.29.0.1 ubuntu1-vm, ubuntu1
	1. vm ip 172.29.0.1 줌 -> 172.28.0.89
7. docker ip 설정 어떻게?
	1. ip는 172.29.0.2 줌 -> 172.29.0.90
8. 6, 7번은 virtual switch에 연결되어 있으므로 옆과 같이 부여
9. 
10. iptables
	1. sudo iptables -A FORWARD -i eno1 -j ACCEPT
	2. 대소 유의
***
# lab 2
1. hypriot OS 설치 문제
	1. 172.29.0.89 pi / pirate / hypriot
	2. 부팅이 안된다.
	3. 1.9 버전은 버전이 RPI 4B 지원 안함
	4. https://github.com/hypriot/image-builder-rpi/releases/download/v1.12.3/hypriotos-rpi-v1.12.3.img.zip
	5. 최신버전에서는 yaml 작동 안함
		1. https://www.joinc.co.kr/w/Site/System_management/NetworkConfiguration network 인터페이스 pi에서 직접 작성 필요