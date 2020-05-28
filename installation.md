1.  I was going for the GCP platform (https://course.fast.ai/start_gcp.html)
Everything was smooth until the middle of step 2.
To create a project I had to add credentials from cli but didn't succeed.
I followed the instructions that say to add api credential but didn't work, instead I've added a project through the site.

2. Since I wanted to use a GPU I had to give my credit to get the upgraded account.
3. Step 3 is also faulty, to create an instance I had to 
    a. Increase the limit on the GCP site (the fastai explain it briefly)
    b. It can take up to 2 days, it took me 10 seconds to get an approval.
    c. The instruction for creating an instance also need to be changed,
          
        The instance required in the tutorial was `n2d-highmem-8` which is not available with GPU in the zones I look.
        So I changed to `n1-highmem-8`, plus I changed the zone to europe-west1-b :
        ```
            export IMAGE_FAMILY="pytorch-latest-gpu" # or "pytorch-latest-cpu" for non-GPU instances
            export ZONE="us-west1-b"
            export INSTANCE_NAME="fastai-us"
            gcloud compute instances create $INSTANCE_NAME \
                            --zone=$ZONE \
                            --image-family=$IMAGE_FAMILY \
                            --image-project=deeplearning-platform-release \
                            --maintenance-policy=TERMINATE \
                            --machine-type="n1-highmem-8" \
                            --accelerator="type=nvidia-tesla-p100,count=1" \
                            --boot-disk-size=200GB \
                            --metadata="install-nvidia-driver=True" \
                            --preemptible
        ```

        after running go to the GCP instance list and press `ssh` and find `View gcloud command` to run the gcp instance.



    d. to ssh to the instance we need to add ssh key, to follow the instructions, but it will fail.Add to the ~/.bashrc the following lines:
            ```
            export INSTANCE_NAME=my-fastai-instance
            export ZONE=us-west1-b
            
            ```
    and send : 
    ```gcloud beta compute ssh --zone "europe-west1-b" "my-fastai-instance" --project "black-network-275911"```
    or the following to start a Jupyter notebook environment with tunneling to the local machine :
    ```gcloud compute ssh --zone "europe-west1-b" "my-fastai-instance" -- -L 8080:localhost:8080```
************ NOW YOU ARE IN THE INSTANCE FROM SSH! ~~~~~~~~~~~~~

4. Setting work environment
    a. To ssh the machine :
     ```
      gcloud compute ssh --zone=$ZONE jupyter@$INSTANCE_NAME -- -L 8080:localhost:8080
      ```


    b. I've managed to access the `crouse-v3` content.
    c. conda install is also wrong use instead:
        ```
        conda install -c fastai fastai
        ```
    d. As explained in the tutorial to access the Jupyter notebook
    write on the local host browser:
    ```
    http://localhost:8080/tree
    ```



                    