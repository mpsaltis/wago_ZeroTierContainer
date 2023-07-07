# wago_ZeroTierContainer
This guide shows how to utilize ZeroTier VPN and network management tools on WAGO Linux Controllers. Zerotier can also be downloaded to a PC and used as a remote monitoring tool for the PLC and Codesys. 

### ZeroTier Configuration
1. Create a ZeroTier Account
2. Create a network and find the Network ID. You will use this ID in your Docker Run Command

![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/665ef967-7437-4692-bb22-25665be0e8e6)


### WAGO Device Configuration
1. Connect the WAGO Controller (Edge Controller, TP600, PFC200)  to the internet. You will also need to set the clock correctly, by enabling NTP client.

   ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/1b31c407-7e13-4c10-b791-9572ff884c7a)
   
3. Enable Docker via the WBM, and reboot the device.
   
   ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/4691ebe0-117c-44cf-b0e3-7f51901c2bfc)
   
6. SSH into the device. You can use the command prompt on your PC, or putty. For the first time connecting, it will ask you to update the password. With command prompt : ssh root@x.x.x.x

 ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/e10a96be-1f3a-4cff-82af-0a3e26cdffb0)
 
   *** Anytime a device is connected to the internet, it is important to change the password for the all users. With WAGO devices FW20 and greater, the users root, admin and user should all be updated with new passwords. To do so, use the the command passwd to update these passwords. Note- This will also update passwords form the WBM and Codesys runtime ***

![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/614f9f85-7128-4ef6-956f-1b17a9822cf9)


9. Enter the following command to pull the docker image, and start a container. Add your networkID at the end of the command shown below.
```
docker run --name myzerotier --restart=unless-stopped --net=host --cap-add NET_ADMIN --device /dev/net/tun zerotier/zerotier:latest **yourNetworkID**
```
![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/2c4b0b95-4fe0-45ba-9836-7757e6001bc2)


5. You should the container start to download and build. Once it is complete, you will see “Sleeping infinitely”. 

  ![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/d0426dd5-3d72-4682-b3e9-ac436e7971ce)

6.	Close the command prompt

7.	After the container is running, you will see a new device populate as a member. To allow this device access to the netowrk, you will need to select the checkbox under the Auth? Column. You can the test the connection abd access the device with the Managed IP address that it was assigned.

![image](https://github.com/mpsaltis/wago_ZeroTierContainer/assets/90796089/dc6eb501-0e62-456a-a308-7bfcdee6ae5a)
