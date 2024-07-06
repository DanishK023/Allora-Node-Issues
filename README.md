
# Allora Basic Node 408 Issue.

Before Begin, Let's see Your Container Running.
```bash
  sudo apt update
```
```bash
  docker ps
```
If Your Container Running, it will show like this.

![ss7](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/56de1805-16bd-438a-9690-1f3eff7026ab)
If it is Not showing Like Above Image, You need to Install Node first, Go [HERE](https://github.com/allora-network/basic-coin-prediction-node) and Install Node First.

# Let's Fix 408 Problem
Note : This is for ``basic-coin-prediction-node``

For Fix the problem you need to go to your Node Directory.  
Use Following Command to GO ``basic-coin-prediction-node``
```bash
  cd $HOME
```
```bash
  ls 
```
![ss1](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/06dfa287-0639-4805-b76b-a8c1f212eceb)
Now Use this command. 
```bash
  cd  basic-coin-prediction-node && ls
```
You will see Following Image
![ss3](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/9a1b365b-33eb-44a0-9044-d6253b54b373)
Enter the Following Command to Edit ``docker-compose.yml`` file.
```bash
  nano docker-compose.yml
```
![ss4](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/9fdd977f-569b-4f26-a4d9-031f24d39e52)

``NOTE : This step is Important Before Process Go through 2-3 Times``  
You will see Following Screen, Change Timeout to ``10s``, Scroll through keypad ``down-arrow`` button go to worker section and Follow below second ScreenShot.  
Change --topic to ``allora-topic-1-worker``  
Now Use Keyboard ``ctrl + x`` after Press ``y``, Now hit ``Enter`` button.

![ss5](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/f8e5e40a-dc75-4db6-bf48-b67ef7a567aa)
![ss6](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/0533b859-f802-413e-b1ce-e6ff1e333657)

Check again You Docker Container is Running by Following Command.  
also Copy all ``CONTAINER_ID`` one-by-one.
```bash
  docker ps
```
![ss7](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/f8aea579-da8e-419c-abc9-dc548a756ee5)

Restart Your All Container by following Command.  change you ``CONTAINER_ID`` to your Container ID.
```bash
  docker restart CONTAINER_ID_1 CONTAINER_ID_2 CONTAINER_ID_3 CONTAINER_ID_4
```
Hit Enter. Wait 10-15 minutes, after that check is container running by ``docker ps`` command.

# Check Node Staus
Follow Commands to Check Nodes Status.
```bash
  nano node-status.sh
```
![ss9](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/494a80bb-3bb6-4b0c-ac36-509ab1ac957a)

Copy ALL Code and Paste in File.
```bash
  curl --location 'http://localhost:6000/api/v1/functions/execute' \
--header 'Content-Type: application/json' \
--data '{
    "function_id": "bafybeigpiwl3o73zvvl6dxdqu7zqcub5mhg65jiky2xqb4rdhfmikswz>    "method": "allora-inference-function.wasm",
    "parameters": null,
    "topic": "1",
    "config": {
        "env_vars": [
            {
                "name": "BLS_REQUEST_PATH",
                "value": "/api"
            },
            {
                "name": "ALLORA_ARG_PARAMS",
                "value": "ETH"
            }
        ],
        "number_of_nodes": -1,
        "timeout": 10
    }
}'
```
![ss10](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/3a8c6acc-e828-4e98-91c7-fca0fddfeae5)

Now Use Keyboard ``ctrl + x`` after Press ``y``, Now hit ``Enter`` button.

Follow Command Further.
```bash
  chmod +x node-status.sh
```
![ss11](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/69f663f2-397c-4b42-96dc-978f8746bfbe)

Last Command, Enter and Wait for response.
```bash
  ./node-status.sh
```
IF node response is ``200`` as per following Image. Voila! Your Node 408 Issue is Fix.
![ss12](https://github.com/DanishK023/Allora-Node-Issues/assets/108999931/52571ea5-7c6d-400c-ac62-ffc9ea7b1417)

