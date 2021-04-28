```bash
sudo docker build . -t test:latest

sudo docker run -itd -v /home/user_abc/tests/container-test/app/:/app/ --name poc-mapping  test:latest
sudo docker run -itd test:latest
#docker run -it --entrypoint=/bash test
sudo docker exec -it poc-mapping bash
```

