# HDFS와 S3비교

## 궁금증

* Hadoop은 Data Warehouse나 Data Lake로 많이 쓰는데, 저장 매체를 HDFS와 S3중 어떤게 더 나을까?

## HDFS\(Hadoop Distributed File System\)란 ?

* Hadoop 애플리케이션을 위한 기본 데이터 스토리지 시스템 
* Apache Software Foundation의 프로젝트 중 하나
* fault-tolerant 파일 시스템으로 상용 하드웨어에서도 실행
* 데이터 위치를 추적하는 NameNode와 데이터를 저장하고 검색하는 DataNode로 구성
* 여러 노드에 replica가 분산 중복 저장되므로 노드 장애 시 데이터 손실을 방지

## Amazon S3\(Simple Storage Service\)란 ?

* 편리한 웹 기반 인터페이스의 객체 스토리지
* AWS의 laas\(Infrastructure as a Service\) 솔루션
* 우수한 확장성, 데이터 가용성, 보안, 성능

## 비교

### Scalability

* HDFS
  * 로컬 스토리지를 기존 노드에 수평적으로 확장할 수 있음
  * 클러스터에 새로운 노드를 추가함으로써 확장할 수 있음
* S3
  * 스토리지를 데이터 사용량에 따라 자동적으로 확장할 수 있음
  * 사실상 스토리지 용량에 제한이 없음

### Durability

* HDFS
  * 데이터 내구성 통계 상 대규모 4,000 노드 클러스터에서 1개의 데이터 블록\(64MB\)를 잃을 확률은 0.00000057
  * 그러나 대부분의 클러스터는 수십개의 노트만 포함되어 있으므로 데이터 손실 가능성이 더욱 큼
* S3
  * 연간 99.999999999%의 내구성 즉, 10,000년에 한 번씩 10,000,000개당 단일 객체 손실 가능성

### Persistence

* HDFS
  * EC2 인스턴스가 중지되면 데이터 유실
  * 단, EBS 볼륨으로 데이터 유지 가능하지만 추가 비용 발생
* S3
  * 항상 지속성을 가짐

### Price

* HDFS
  * 데이터 무결성을 위해 기본적으로 데이터 블록 단위로 3개의 복사본을 저장하여 비용이 3배
  * 데이터 복사본을 줄일 수 있지만 복사본이 하나인 경우 데이터 무결성에 지장을 줄 수 있음
* S3
  * 자체에서 데이터 백업 문제를 처리하므로 실제 필요한 스토리지에 대해서만 비용 지불
  * 압축 파일 저장을 지원하여 스토리지 비용 절감

### Performance

* HDFS
  * 동일한 시스템에 저장되고 처리되기 때문에 액세스 및 처리 속도 매우 우수
* S3
  * 상대적으로 지연 시간이 높고, 데이터 처리량은 더 낮음
* I/O Test
  * m1.xlarge 인스턴스 \(4개의 임시 디스크\) 기준

    ![I/O Test](https://user-images.githubusercontent.com/60086878/102498086-de261880-40bc-11eb-9cb8-8308d1783eac.png)

### Security

* HDFS
  * Kerberos를 통한 사용자 인증과 파일 시스템 권한을 통한 권한 부여 가능
  * 클러스터를 여러 NameSpace로 분할하여 특정 사용자에게 데이터 액세스 제한 가능
  * SSL을 통해 Amazon 인스턴스 제한 가능
* S3
  * 보인 기능 내장으로 사용자 인증 지원
  * 버킷과 객체 소유자만이 데이터에 액세스 할 수 있음
  * 버킷 정책과 ACL\(Access Control Lists\)을 통해 사용자와 그룹에 추가 권한 부여 가능
  * SSL을 통해 데이터 암호화 가능

### Limitations

* HDFS
  * 모든 크기의 파일을 저장할 수 있지만 매우 작은 파일을 저장하는데 문제가 있음
  * 데이터를 해당 클러스터의 시스템에서만 사용할 수 있고, 외부 인스턴스에서 사용 불가
* S3
  * 데이터는 Hadoop 클러스터와 독립적이며 여러 클러스터에서 동시 처리 가능하나, 최대 파일 크기가 5GB에 불과함 
  * Parquet이나 ORC와 같은 Hadoop 스토리지 형식을 사용할 수 없음

## 정리

각자 장단점이 있고, 아래 용도에 맞게 사용하는게 맞는듯 하다.

* HDFS
  * 빠른 처리속도와 파일 크기와 스토리지 형식에 제한이 없어야하는 경우 유리
* S3
  * 뛰어난 확장성, 지속성 그리고 저렴한 비용을 요하는 경우 유리

