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

copy stuff from s3:
```

cd tDSIN/ ; git pull ; git checkout cuda_aws_si_option; conda activate tfastai; pip install -e .


aws s3 cp --recursive s3://dsin-us/data_scene_flow_multiview ~/tDSIN/src/dsin/data/data_scene_flow_multiview/ &
aws s3 cp --recursive s3://dsin-us/data_data_stereo_flow_multiview ~/tDSIN/src/dsin/data/data_stereo_flow_multiview/ &
aws s3 cp --recursive s3://dsin-us/disc_data/data_scene_flow_multiview ~/tDSIN/src/dsin/disc_data/data_scene_flow_multiview/ &
aws s3 cp --recursive s3://dsin-us/disc_data/data_stereo_flow_multiview ~/tDSIN/src/dsin/disc_data/data_stereo_flow_multiview/ &
aws s3 cp  s3://dsin-us/models/200816MAE-l2reg-res-si-new-normalize-4.pth ~/tDSIN/src/dsin/data/models/ &
aws s3 cp  s3://dsin-us/models/200816MAE-l2reg-baseline-1.pth ~/tDSIN/src/dsin/data/models/ &


```


2020-09-04try2MSSIM-l2reg-baseline-bpp0p30-16'
'2020-09-05sinet-MAE-l2reg-si-nofeat-bpp0p30-3