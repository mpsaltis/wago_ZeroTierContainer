# wago_ZeroTierContainer
This guide shows how to utilize ZeroTier VPN and network management tools on a WAGO Linux Controller


1. Connect the WAGO Controller (Edge Controller, TP600, PFC200)  to the internet. You will also need to set the clock correctly, by enabling NTP client.
   ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/1b31c407-7e13-4c10-b791-9572ff884c7a)
2. Enable Docker via the WBM, and reboot the device.
   ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/4691ebe0-117c-44cf-b0e3-7f51901c2bfc)
3. SSH into the device. You can use the command prompt on your PC, or putty. For the first time connecting, it will ask you to update the password. With command prompt : ssh root@x.x.x.x
  ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/e10a96be-1f3a-4cff-82af-0a3e26cdffb0)
4. Enter the following command to pull the docker image, and start a container. Add your networkID at the end of the command shown below.
 
docker run --name myzerotier --rm --net=host --cap-add NET_ADMIN --device /dev/net/tun zerotier/zerotier:latest yourNetoworkID

  ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/2912e0b3-8ffa-4d42-99bf-45be8ce1b9b1)

5. You should the container start to download and build. Once it is complete, you will see “Sleeping infinitely”. 

  ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/d0426dd5-3d72-4682-b3e9-ac436e7971ce)

6.	Close the command prompt
