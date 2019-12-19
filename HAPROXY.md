

# Hproxy 주요옵션	
    # Default SSL material locations
	ca-base /etc/ssl/certs
	crt-base /etc/ssl/private

# Haproxy 인증서 만들기 순서
cat COMODORSADomainValidationSecureServerCA.crt COMODORSAAddTrustCA.crt AAACertificateServices.crt > intermediate.pem
cat hub_webnori_com_SHA256WITHRSA.key >> hub_webnori_com.pem
cat hub_webnori_com.crt >> hub_webnori_com.pem
cat ChainCA/intermediate.pem >> hub_webnori_com.pem

# 인증서 복사
sudo cp hub_webnori_com.pem /etc/haproxy
sudo cp hub_webnori_com.pem /etc/ssl/private
sudo cp *.crt /etc/ssl/certs


# Haproxy
    
    /etc/init.d/haproxy restart
    systemctl status haproxy.service
