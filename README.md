# breez_lnd_test


build the image   
`docker build --file Dockerfile_mainnet_v12 --tag breez_v12_mainnet_v2 .`  
run with a volume   
`docker run -it -p 10009:10009 -v breez_lnd_test:/root/.lnd breez_v12_mainnet_v2`  
once the container is up, start lnd   
`lnd/lnd &`  
   
in another termial  
`docker ps` to get the container id  
exec into the container   
`docker exec -it -w /lnd <containerID> /bin/bash`  
once in create wallet `lncli create`  
  
Running this for the first time should work no problem  
 
   
Now
* stop and exit the container  
* delete the stopped container `docker rm <containerID>`  
* delete the named volume: `docker volume rm breez_lnd_test`  
   
at this time there should be no files leftover from the lnd run  
so let's run the image again (should be fresh)  
  
`docker run -it -p 10009:10009 -v breez_lnd_test:/root/.lnd breez_v12_mainnet_v2`      
once the container is up, start lnd
`lnd/lnd &`

in another termial
`docker ps` to get the container id
exec into the container
`docker exec -it -w /lnd <containerID> /bin/bash`
once in create wallet `lncli create`
  

now the terminal running LND should report the error   
`unable to create RPC server: failed to read root key ID from context`  


