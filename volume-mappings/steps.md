## Volume mapping tests

### 
Creating basic structure and files with dummy content:

```bash
mkdir -p /home/user_abc/tests/container-test
cd /tests/container-test/
mkdir -p base/folder1
mkdir -p base/folder2
echo "some content" > base/test1.txt
echo "some content at folder1" > base/folder1/test1.txt
echo "some content at folder2" > base/folder2/test2.txt

mkdir app
```

### Docker operations
```bash
sudo docker build . -t test:latest

sudo docker run -itd -v /home/user_abc/tests/container-test/app/:/base/app/ --name poc-mapping  test:latest
sudo docker ps
#sudo docker run -itd test:latest
#docker run -it --entrypoint=/bash test
sudo docker exec -it poc-mapping bash
```

### Tests
```bash
sudo docker exec -it poc-mapping bash

#into container
ls app
echo "something ..." > app/some1.txt
mkdir -p app/package/python
mkdir -p app/package/R
echo "something python 1..." > app/package/python/somepy1.txt
echo "something R 1..." > app/package/R/someR1.txt
ls app
exit

# into host again
ls app
ls app/package/R/
#

```
