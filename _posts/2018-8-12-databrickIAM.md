---
layout: post
title: Web
---
IAM 설정을 사용하려면 다음 개념을 이해 해야 한다.
IAM은 권한설정을 관리할 수 있는 json일뿐이며, 이를 통해 접근하려면 role ARN을 각 계정이 가지고 있어야하며,
각 서비스에 해당 role ARN을 principal로 지정해 줘야 한다.

1.cross account role
https://docs.databricks.com/administration-guide/account-settings/aws-accounts.html
databrick 이 aws에 접속할 수 있도록 허용해주는 IAM role 이다
나중에 이 IAM role 이 기본이 되어 databrick 연결이 s3 storage에 들어갈 수 있게 해준다

2.s3 스토리지 사용 권한 IAM role 생성과 s3 permission에 해당 내용 지정
https://docs.databricks.com/administration-guide/cloud-configurations/aws/iam-roles.html
https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/dev/example-walkthroughs-managing-access-example2.html
cross account role에 s3를 사용하기 위해 스토리지 사용 권한을 설정한 별도의 IAM role을 만든후 추가하고
s3 permission에 권한을 설정한 후 cross acccount role을 해당 permission에 추가한다.

3. 상기 내용 모두가 databrick에 설정되어야 한다.
   1번은 management console에 AWS Account Settings 에 적용되어야 하고
   2번은 클러스터 start시 설정되어야 한다.
   
참고로 아래 페이지는 오류가 있는데, step 2에 5번은
<s3-cross-account-role> with the role you created in Step 1 이 아니라
<s3-cross-account-role> with the role you created in https://docs.databricks.com/administration-guide/account-settings/aws-accounts.html
이다.
https://docs.databricks.com/administration-guide/cloud-configurations/aws/iam-roles.html
