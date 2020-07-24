ssh -i ~/Downloads/london_ami_key.pem ubuntu@35.178.142.208
change - sudo chmod 644 ~/.ssh/config 
set the {{config}} file contents to :
Host personal
    HostName ec2-35-178-142-208.eu-west-2.compute.amazonaws.com
    User ubuntu
    IdentityFile ~/Downloads/london_ami_key.pem


Host <host name in vscode (arbitrary)>
    HostName <dns public name of my instance>
    User <user in the instance>
    IdentityFile <pem file with full path>