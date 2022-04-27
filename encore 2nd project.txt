# encore 2nd 프로젝트 문서
## 컨트롤 노드 준비
### ansible 설치 (컨트롤 노드)
1. 기본 repository에서는 ansible, remi repo 설치가 불가능하여 Extra Packages for Enterprise Linux (EPEL) 설치
``` bash
$ sudo yum install -y epel-release
```
2. ansible 설치
``` bash
$ sudo yum install -y ansible
```

### wordpress 파일 준비 (컨트롤 노드)
1. wordpress 파일 준비를 위한 wget 설치
```bash
$ sudo yum install -y wget
```
2. wordpress 다운로드
```bash
$ wget https://wordpress.org/wordpress-5.9.3.tar.gz
```
3. wordpress.tar.gz 압축 풀기
```bash
$ tar -xzvf wordpress-5.9.3.tar.gz  
```
4. wordpress 설정파일 복사 밑 j2템플릿 제작
```bash
$ cp ~/wordpress/
$ cp ~/wordpress/wp-config-sample.php ~/project/web-server/templates/wp-config.php.j2
```
데이터베이스 관련 구문을 템플릿 형식에 맞게 변경.
변수 이름은 `database`
```jinja2
// ** Database settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define( 'DB_NAME', {{ database["name"] }} );

/** Database username */
define( 'DB_USER', {{ database["user"] }} );

/** Database password */
define( 'DB_PASSWORD', {{ database["password"] }} );

/** Database hostname */
define( 'DB_HOST', {{ database["host"] }} );

```
5. 파일 배포 준비를 위해 wordpress 아카이브 파일을 files폴더로 이동
```bash
$ mv ~/wordpress-5.9.3.tar.gz ~/project/web-server/files/
```


### ansible playbook 작성
1. ansible 프로젝트를 위한 폴더 및 role 생성
```bash
$ cd ~
$ mkdir project
$ cd project
$ ansible-galaxy init web-server --init-path seb-server
```
2. 동적 인벤토리 설정
```
```
3. 




## 메모중….
### 플레이북 작성해야함
1. php설치
2. httpd설치
3. 워드프레스 아카이브 파일 복사
4. 워드프레스 설정파일도 복사
5. 서비스 업
6. 동적 인벤토리 사용 aws_ec2.yml
```
ansible-doc -t inventory aws_ec2 로 확인
sudo yum install - y python3
sudo yum install python-boto3 설치
```
inventory_aws_ec2.yml
```yaml
plugin: aws_ec2
aws_profile: "Default"

filters: enviroment: dev
```
aws cli 설치
```bash
$ sudo yum install -y unzip

$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install
```
aws configure로 aws로그인
```bash
$aws configure
```
7. 
	* PHP설치 방법 
``` bash
# PHP설치를 위해 remi repo설치
$ sudo rpm -ivh https://rpms.remirepo.net/enterprise/remi-release-7.rpm

# PHP 7.4버전 설치를 위해 remi-php74 repository 활성화
$ sudo yum install -y yum-utils
$ sudo yum-config-manager --enable remi-php74

#더 진행해야댐!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
```




