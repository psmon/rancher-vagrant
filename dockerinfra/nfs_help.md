# nfs 스토리지 추가

용도: 도커컨테이너가 사용되는 데이터 영역을, 특정 스토리지에 중앙화하여 백업및 관리하기위한 Tools  

# nfs 서버 구성

sudo apt-get update
sudo apt-get install nfs-kernel-server
sudo mkdir /media/psmon/DataB/docker_data
sudo chown nobody:nogroup /media/psmon/DataB/docker_data

sudo vi /etc/exports
        # NFS for Docker
        /media/psmon/DataB/docker_data 192.168.56.0/24(rw,sync,no_root_squash,no_subtree_check)

        /media/psmon/DataB/docker_data
                192.168.56.0/24
        
sudo systemctl restart nfs-kernel-server

# Rancher nfs 스토리지 추가
카탈로그에서 NFS 드라이브 검색

NFS_SERVER: 192.168.56.1
MOUNT_DIR: /docker_data
MOUNT_OPTS: ',nfsvers=4
ON_REMOVE: purge(제거) or retain(유지) - 컨테이너가 제거될때 제거할지 유지할지에대한 옵션 
