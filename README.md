이것저것 써두는곳

- bash
bash 스크립트 작성한 것들 나열 해둠

- s3_update
AWS기준으로 작성되었고 파이선 버전은 3.6이상에서 돌려야함
UI는 ktinter를 사용했고 boto3를 주로 이용해 작성함
AWS에 s3에서 디랙터리 별로 권한을 줘야하며 그 디랙터리를 쓸 IAM 사용자가 필요하다.
처음에 켜지면 로그인 버튼을 눌러서 aws_info.py에서 정보 를 받아와 로그인됨
(처음엔 IAM 엑세스키 등 을 가르쳐 준다음 써 넣는 방식이였는데 
사용자들이 힘들거 같다고해서 걍 받아오는 형식으로 변경)
로그인 되면 s3에 디랙터리에 있는 파일들이 나열 된다.
파일을 올리면 내 창에서 선택이 가능하며 실수로 잘못 올리면 지울 수 있다.
Send 버튼을 누르면 프로세스가 람다 함수로 실행되고 특정 버튼은 disable된다.
보내는 중 끊을 수 도 있고 동안 프로그래스 바가 올라가면서 몇 퍼센트 남았는지 보여준다.


- terraform0
오하이오에 있는 리전에 VPC 하나를 만들고 서브넷 3개와 라우팅테이블로 연결을 하여 인터넷 게이트웨이 연결 함
그리고  EC2 쪽은 서브넷 각 존에 2개 씩 올리고 ELB 설정함 
한쪽은 ALB 설정을 하고 내용은 HTTP에서 HTTPS 리다이랙션이며 타겟은 자기자신이 속한 LB로 설정
다른쪽은 L4 로드밸런싱 구성함 80포트로 받으면 바로 자기 LB 그룹에다가 포워딩 시킴
이대로 받아가면 실행 절대 안되고 이거 기반 수정을 해야함 


- terraform1
PublicSubnet과 PrivateSubnet 만들어서 PrivateSubnet에는 NAT 설정과 Elacitc IP 연결

       
