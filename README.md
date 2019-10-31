export PROJECT_ID='as471assignment'

gcloud iam service-accounts create ssh-account --project $PROJECT_ID \
   --display-name "ssh-account"

gcloud compute networks create ssh-example --project $PROJECT_ID


gcloud compute firewall-rules create ssh-all --project $PROJECT_ID \
   --network ssh-example --allow tcp:22

gcloud compute instances create target --project $PROJECT_ID \
   --zone us-central1-f --network ssh-example \
   --no-service-account --no-scopes \
   --machine-type f1-micro --metadata=enable-oslogin=TRUE

gcloud compute instances add-iam-policy-binding target \
   --project $PROJECT_ID --zone us-central1-f \
   --member serviceAccount:ssh-account@$PROJECT_ID.iam.gserviceaccount.com \
   --role roles/compute.osAdminLogin

gcloud compute instances create source \
   --project $PROJECT_ID --zone us-central1-f \
   --service-account ssh-account@$PROJECT_ID.iam.gserviceaccount.com  \
   --scopes https://www.googleapis.com/auth/cloud-platform \
   --network ssh-example --machine-type f1-micro

*****Private key*****
A private key, also known as a secret key, is a variable in cryptography that is used with an algorithm to encrypt and decrypt code. Secret keys are only shared with the key’s generator, making it highly secure. Private keys play an important role in symmetric cryptography, asymmetric cryptography and cryptocurrencies.

*****Public Key*****
A public key is created in public key encryption cryptography that uses asymmetric-key encryption algorithms. Public keys are used to convert a message into an unreadable format. Decryption is carried out using a different, but matching, private key. Public and private keys are paired to enable secure communication.

*****Why do we need to configure SSH*****

SSH is a Swiss army knife of connectivity. It replaces at least 4 programs that I know of:

telnet,ftp,vnc (partly), vpn (partly) . These days telnet and ftp are discouraged because they are insecure , while ssh is secure due to packet encryption. Password or Key based login can be used for remote login. If you need to run a graphics application on the remote *nix system, you can do so using ssh -Y <system name>. Of course, the remote system must be configured to accept this. You can also use the ssh host as a gateway and forward ports to/from remote systems. it can be simpler than setting up a VPN and also leverages SSH’s functionality.

Finally Windows systems can join the fun as either a client or server. The server side is most commonly setup using cygwin. Putty (a free ssh Windows client) is most commonly used the client application of choice. You can even display remote X on your Windows applications with helper apps such as Xming.



**privet and public key use for google cloud platform
ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEAsllXLShxHgTzSJeM1ZVEGThxzGq8ZWYt+Ou44JQu+abdoV/9VwDT90VNMEhEBcwHyPhbFdPFWRIVCG/f8S0Ys6IUVBhNGjt6TDaKLiMZ3Pxw9Hmd6M78mSbgENcpSRPLr0ZbPr49byt6Lzf46sdB0yXxPFenPtRXMY7eXK9Myuc2hxatSFt+UnAC9yzo+twNUphuLx+iSaT/+tyqUXvwBl9nu0tuvgjh+GS8zsAUkGcxE1RgrpzJNMT8vSnIBSDE3qdtE0LgJYp79M6YuBNGKp1h00wdvyV9f/NkQr7odCiKzviR5V+VD9QZYV790JplPceER6s+JhDrDJmt9BnEYQ== rsa-key-20191031

echo "Hello, world! The time is $(date)."
FROM alpine
COPY quickstart.sh /
CMD ["/quickstart.sh"]

**Use of docker
Docker is a tool design to make it eacier to create ,deploy and run application by using containers .Containers allow a developer to package up an application
with all of the parts it needs. Such as libraries and other dependencies and ship it all out as one package


