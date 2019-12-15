
# 설치

    sudo apt-get install nfs-kernel-server nfs-common rpcbind

    sudo /etc/init.d/portmap restart


# 공유 디렉토리
 
    sudo mkdir /media/psmon/DataB/docker_data
    sudo chown nobody:nogroup /media/psmon/DataB/docker_data
    sudo chown 777 /media/psmon/DataB/docker_data

    # 마운팅 주소를 짧게
    ln -s /media/psmon/DataB/docker_data /docker_data

    
# sudo vi /etc/exports
 
    # NFS for Docker
    /docker_data 192.168.56.0/24(rw,sync,no_root_squash,no_subtree_check)
    
# Restart       

    sudo systemctl restart nfs-kernel-server

# Rancer NFS-Stack 설치

    server : 192.168.56.1
    dir : docker_data
    version : nfs3

# test

    mkdir test
    sudo mount -t nfs 192.168.56.1:/docker_data ~/test
