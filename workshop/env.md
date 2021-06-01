# 개발환경
## 동작 확인한 버전
 * PX4 Firmware
   * v1.11.1 ~ 1.11.2
   * commit : e0f6c220
 * Avoidance
   * 2020. 11. 3.
   * commit : 8a957267

## 설치
 * Ubuntu 18.04
   * [다운로드](https://releases.ubuntu.com/18.04/)
 * PX4 설치
```
> git clone https://github.com/PX4/PX4-Autopilot
> cd PX4-Autopilot/Tools/setup
> ./ubuntu.sh
```

 * ROS 설치 (melodic)
```
> 
```

 * Avoidance 설치
```bash
> 
```

 * Visual Studio Code
```
$ sudo apt-get install curl
$ sudo sh -c 'curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /etc/apt/trusted.gpg.d/microsoft.gpg'
$ sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
$ sudo apt update
$ sudo apt install code

```
 * Chrome
```
> wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
> sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
> sudo apt-get update
> sudo apt-get install google-chrome-stable
> sudo rm -rf /etc/apt/sources.list.d/google.list
```
