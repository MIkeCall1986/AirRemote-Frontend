<p align="center">
  <img width="340" src="src/assets/imgs/logo-black.png#gh-light-mode-only" alt="AirRemote Logo">
  <img width="340" src="src/assets/imgs/logo-white.png#gh-dark-mode-only" alt="AirRemote Logo">
</p>
<h2 align="center">AirRemote Frontend Repository ⚡</h2>
<p align="center">
    <a href="/LICENSE"><img alt="GPL-V3.0 License" src="https://img.shields.io/badge/License-GPLv3-orange.svg"></a>
    <a href="https://github.com/jugeekuz/AirRemote-Frontend/graphs/contributors"><img alt="Contributors" src="https://img.shields.io/github/contributors/jugeekuz/AirRemote-Frontend?color=green"></a>
<!--     <a href="https://www.linkedin.com/in/anastasiosdiamantis"><img alt="Connect on LinkedIn" src="https://img.shields.io/badge/Connect%20on-LinkedIn-blue.svg"></a> -->
</p><br>

Turn your old remote-controlled devices into smart devices! With AirRemote, you can turn any legacy device that can be controlled by an IR remote, into a remotely accesible smart device.

<p align="center">
    <img src="./src/assets/imgs/demo.gif" alt="AirRemote Short Demo" width="320">
</p>


--- 
## 📝  Description


AirRemote is a solution designed to modernize legacy remote-controlled devices by making them smart and remotely accessible. AirRemote operates as a universal remote emulator. It works by capturing the infrared (IR) signals from any remote control—regardless of how rare or obscure—and storing them for later use. You can then replay those commands remotely through the web interface (or through automated routines) enabling you to perform actions such as open the A/C or your heater on your way back, finding your house in the perfect temperature when you arrive, or just keep all your remotes in one place without needing to search for them every time.

## 🔧 Features 
- Record the IR signals by simply pressing the buttons of their existing remote control onto the AirRemote device.
- Replay the stored signals on command via a web interface.
- Create automations to perform a set of operations (such as open lighting, A/C etc.) at specific times.
- Give the device to a friend, with the capability to initialize the device and provide credentials through a Captive Portal interface.
- Manage, Delete, Reorder your favourite devices through the web interface.

With these capabilities, AirRemote turns virtually any device with an IR remote into a smart, remotely controllable appliance.

## 🎥 Demo
<!-- <div align="center" style="display: flex; flex-direction: row; justify-content: center; gap: 1px; flex-wrap: wrap;">
  <div style="flex: 0 0 200px;">
    <h4>Login & Dashboard</h4>
    <img src="./src/assets/imgs/login.gif" alt="Demo 1" width="200">
  </div>
  <div style="flex: 0 0 200px;">
    <h4>Add Remote and Execute</h4>
    <img src="./src/assets/imgs/demo.gif" alt="Demo 2" width="200">
  </div>
        <div style="flex: 0 0 200px;">
            <h4>Create Automations</h4>
            <img src="./src/assets/imgs/automations.gif" width="200">
        </div>
        <div style="flex: 0 0 200px;">
            <h4>Register Devices</h4>
            <img src="./src/assets/imgs/wifi-setup.gif" width="200">
        </div>
        <div style="flex: 0 0 200px;">
            <h4>Reorder & Edit tiles</h4>
            <img src="./src/assets/imgs/rearrange.gif" width="200">
        </div>
</div> -->
<div align="center">
    <table>
    <tr>
        <td>
            <div style="flex: 0 0 300px;">
                <h4>Login & Dashboard</h4>
                <img src="./src/assets/imgs/login.gif" alt="Demo 1" width="300">
            </div>
        </td>
        <td>
            <div style="flex: 0 0 300px;">
                <h4>Add Remote and Execute</h4>
                <img src="./src/assets/imgs/demo.gif" alt="Demo 2" width="300">
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div style="flex: 0 0 300px;">
                <h4>Create Automations</h4>
                <img src="./src/assets/imgs/automations.gif" width="300">
            </div>
        </td>
        <td>
            <div style="flex: 0 0 300px;">
                <h4>Register Devices</h4>
                <img src="./src/assets/imgs/wifi-setup.gif" width="300">
            </div>
        </td>
    </tr>
    <tr>
        <td>
            <div style="flex: 0 0 300px;">
                <h4>Reorder & Edit tiles</h4>
                <img src="./src/assets/imgs/rearrange.gif" width="300">
            </div>
        </td>
    </tr>
    </table>
</div>

## 🌟 Project Overview

The **AirRemote** project is divided into three main components. Each part contains instructions on how to deploy / install it:

- [**Embedded Device:**](https://github.com/jugeekuz/AirRemote-Embedded) 
    - A C/C++ PlatformIO project, involving ESP32-based unit with an IR receiver and 8 powerful IR blasters. It records IR signals from any remote control and replays them across the room, enabling universal compatibility.
    
- [**Serverless Backend:**](https://github.com/jugeekuz/AirRemote-Backend) 
    - A Python project using Serverless framework to deploy a scalable AWS-based backend powered by Lambda, DynamoDB, API Gateway, and EventBridge. It ensures secure command storage, user authorization, and efficient routing between the web interface and devices.

- [**Frontend (This Repository):**](https://github.com/jugeekuz/AirRemote-Frontend) 
    - A React JS project providing an application for managing devices, saving IR commands, authenticating users and creating powerful automation routines—all accessible through a sleek web interface.

---

## ⚙️ Installation and deployment
### 📦 Prerequisites

1. Make sure you have npm 10.0+ installed.
    ```bash
    npm -v
    ```

2. Make sure you have [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) installed and configured:
    ```bash
    aws --v
    aws s3 ls
    ```

### 🚀 Deployment to AWS

1. #### Create S3 Bucket
    ```bash
    aws s3api create-bucket --bucket <your-bucket-name> --region <your-region-id> --create-bucket-configuration LocationConstraint=<your-region-id>
    ```
3. #### Clone this repository:
    ```bash
    git clone https://github.com/jugeekuz/AirRemote-Frontend
    ```
4. #### Install dependencies:
    ```bash
    npm install
    ```
5. #### Add .env file 
    - Copy the `.env` file produced from the deployment of the [*Serverless Backend*](https://github.com/jugeekuz/AirRemote-Backend) to the root directory of this project (if you don't have it yet you can add it later and redeploy).

6. #### Build the production build of the project:
    ```bash
    npm run build
    ```
7. #### Upload your files
    ```bash
    aws s3 sync ./dist s3://<your-bucket-name>
    ```
8. #### Enable Static Website Hosting
    ```bash
    aws s3 website s3://your-bucket-name/ --index-document index.html --error-document index.html
    ```

9. #### Configure Route 53
    1. Create a Hosted Zone (Change `unique-string` to some unique value):
        ```bash
        aws route53 create-hosted-zone --name <hosted-zone-name> --caller-reference unique-string
        ```

    2. Retrieve the NameServers and update them in your domain registrar (verify that the name server change took place using a whois service).

10. #### Request an SSL Certificate using AWS ACM
    - Request a Certificate (region has to be `us-east-1`) and keep the CertificateArn output:
        ```bash
        aws acm request-certificate --domain-name <your-domain-name> --validation-method DNS --region us-east-1
        ```

11.  #### Create DNS validation records in Route 53
    1. Retrieve the necessary CNAME entries from ACM (use the `CertificateArn` from previous step):
        ```bash
        aws acm describe-certificate --certificate-arn <your-certificate-arn> --region us-east-1
        ```

    2. Save the following config in `tmp/acm_validation_config.json` (replace `<CNAME_name_from_acm>` and `<CNAME_value_from_acm>` w/ the values retrieved from the output of previous command under `ResourceRecord`) :
        ```json
        {
            "Changes": [
                {
                    "Action": "UPSERT",
                    "ResourceRecordSet": {
                        "Name": "<CNAME_name_from_acm>" ,
                        "Type": "CNAME",
                        "TTL": 300,
                        "ResourceRecords": [{"Value": "<CNAME_value_from_acm>"}]
                    }
                }
            ]
        }
        ```

    3. Add the CNAME record to Route 53 (replace the `HOSTED_ZONE_ID` w/ value from step 3.1):
        ```bash
        aws route53 change-resource-record-sets --hosted-zone-id <HOSTED_ZONE_ID> --change-batch file://tmp/acm_validation_config.json
        ```

12. #### Verify ACM Certificate Validation Status
    After some time, verify that the ACM Certificate `Status` is `ISSUED` and `ValidationStatus` is `SUCCESS`. Give it some time if it isn't (it could take up to an hour).
    ```bash
    aws acm describe-certificate --certificate-arn <your-certificate-arn> --region us-east-1
    ```

13. #### Create CloudFront distribution
    1. Create an Origin Access Control and save it to `tmp/origin_access_control_config.json`
        ```json
        {
            "Name": "air-remote-access-control",
            "Description": "OAC for AirRemote bucket",
            "SigningProtocol": "sigv4",
            "SigningBehavior": "always",
            "OriginAccessControlOriginType": "s3"
        }
        ```
    
    2. Publish it and retrieve the Id that is displayed in the response
        ```bash
        aws cloudfront create-origin-access-control --origin-access-control-config file://tmp/origin_access_control_config.json
        ```

    3. Create a caching policy and save it to `tmp/caching_policy.json`
        ```json
        {
            "Name": "AirRemoteCustomCachePolicy",
            "DefaultTTL": 86400,
            "MinTTL": 0,
            "MaxTTL": 31536000,
            "ParametersInCacheKeyAndForwardedToOrigin": {
                "EnableAcceptEncodingGzip": true,
                "EnableAcceptEncodingBrotli": true,
                "HeadersConfig": {
                    "HeaderBehavior": "none"
                },
                "CookiesConfig": {
                    "CookieBehavior": "all"
                },
                "QueryStringsConfig": {
                    "QueryStringBehavior": "all"
                }
            }
        }
        ```

    4. Publish the cache policy and retrieve the Id in the response to use on the next step.
        ```bash
        aws cloudfront create-cache-policy --cache-policy-config file://tmp/caching_policy.json
        ```

    5. Create the distribution config and save it to `tmp/cloudfront_distribution_config.json` and replace `<your-domain>`, `<ORIGIN-ACCESS-CONTROL-ID>`, `<CACHE_POLICY_ID>` and `<ACM_CERTIFICATE_ARN>` with your values retrieved from previous steps.
        ```json
        {
            "CallerReference": "'CLOUDFRONT_AIRREMOTE_DISTRIBUTION'",
            "Comment": "Air Remote CloudFront Distribution",
            "Enabled": true,
            "Aliases": {
                "Quantity": 1,
                "Items": ["<your-domain>"]
            },
            "Origins": {
                "Quantity": 1,
                "Items": [
                {
                    "Id": "air-remote-origin",
                    "DomainName": "<your-domain>.s3.eu-central-1.amazonaws.com",
                    "OriginAccessControlId": "<ORIGIN-ACCESS-CONTROL-ID>",
                    "S3OriginConfig": {
                    "OriginAccessIdentity": ""
                    }
                }
                ]
            },
            "DefaultCacheBehavior": {
                "TargetOriginId": "air-remote-origin",
                "ViewerProtocolPolicy": "redirect-to-https",
                "AllowedMethods": {
                "Quantity": 2,
                "Items": ["GET", "HEAD"]
                },
                "CachePolicyId": "<CACHE_POLICY_ID>"
            },
            "ViewerCertificate": {
                "ACMCertificateArn": "<ACM_CERTIFICATE_ARN>",
                "SSLSupportMethod": "sni-only",
                "MinimumProtocolVersion": "TLSv1.2_2021"
            },
            "Restrictions": {
                "GeoRestriction": {
                "RestrictionType": "none",
                "Quantity": 0
                }
            },
            "CustomErrorResponses": {
                "Quantity": 2,
                "Items": [
                    {
                    "ErrorCode": 403,
                    "ResponsePagePath": "/index.html",
                    "ResponseCode": "200",
                    "ErrorCachingMinTTL": 300
                    },
                    {
                    "ErrorCode": 404,
                    "ResponsePagePath": "/index.html",
                    "ResponseCode": "200",
                    "ErrorCachingMinTTL": 300
                    }
                ]
            },
            "HttpVersion": "http2",
            "IsIPV6Enabled": true,
            "DefaultRootObject": "index.html",
            "WebACLId": ""
        }
        ```
    6. Create the distribution:
        ```bash
        aws cloudfront create-distribution --distribution-config file://tmp/cloudfront_distribution_config.json
        ```

14. #### Create S3 bucket policy
    1. Create the following bucket policy in `tmp/s3_bucket_policy.json` and replace w/ values from previous steps.
        ```json
        {
            "Version": "2008-10-17",
            "Id": "PolicyForCloudFrontPrivateContent",
            "Statement": [
            {
                "Sid": "AllowCloudFrontServicePrincipal",
                "Effect": "Allow",
                "Principal": {
                    "Service": "cloudfront.amazonaws.com"
                },
                "Action": "s3:GetObject",
                "Resource": "arn:aws:s3:::<your-domain>/*",
                "Condition": {
                    "StringEquals": {
                        "AWS:SourceArn": "<CLOUDFRONT_ARN>"
                    }
                }        
            }
            ]
        }
        ```

    2. Attach the policy to S3
        ```bash
        aws s3api put-bucket-policy --bucket <your-domain> --policy file://tmp/s3_bucket_policy.json
        ```

15. #### Map Domain Name to Cloudfront distribution
    1. Get the Cloudfront distribution URL and Route 53 Hosted Zone Id through the following commands (present in `DomainName` / `Id` ):
        ```bash
        aws cloudfront list-distributions
        aws route53 list-hosted-zones
        ```

    2. Create a file `tmp/route_53_record.json` and paste the following:
        ```json
        {
            "Comment": "A record for CloudFront distribution",
            "Changes": [
                {
                    "Action": "UPSERT",
                    "ResourceRecordSet": {
                        "Name": "<your-domain>",
                        "Type": "A",
                        "AliasTarget": {
                            "HostedZoneId": "Z2FDTNDATAQYW2",
                            "DNSName": "<CLOUDFRONT_DOMAIN_NAME>",
                            "EvaluateTargetHealth": false
                        }
                    }
                }
            ]
        }
        ```

    3. Apply the change through the CLI:
        ```bash
        aws route53 change-resource-record-sets --hosted-zone-id "<HOSTED-ZONE-ID>" --change-batch file://tmp/route_53_record.json
        ```

    4. Verify that the change took place by checking if `Status` is `INSYNC` (change `<CHANGE_ID>` with the output of the previous command)
        ```bash
        aws route53 get-change --id <CHANGE_ID>
        ```
16. #### Deploy backend and provide .env file
    1. If you haven't already, deploy the [AirRemote Backend](https://github.com/jugeekuz/AirRemote-Backend).

    2. In the `/output` folder of the serverless project (after deployment) there will be a `.env` file containing the API endpoints. Copy it to the root directory of this project.

    3. Rebuild the project:
        ```bash
        npm run build
        ```

    4. Redeploy to AWS S3:
        ```bash
        aws s3 sync ./dist s3://<your-bucket-name>
        ```

    5. Create a cache invalidation for the cache to be purged in CloudFront:
        ```bash
        aws cloudfront create-invalidation --distribution-id <CLOUDFRONT_DISTRIBUTION_ID> --paths "/*"
        ```

17. #### Create Custom Domain Mappings for API Gateway
    1. Obtain your ACM Certificate ARN:
        ```bash
        aws acm request-certificate --domain-name "*.<YOUR-DOMAIN>" --validation-method DNS --output text  --query 'CertificateArn' --region <YOUR-REGION>
        ```
    2. Wait for the Certificate to be issued (check `Status` to be `ISSUED`):
        ```bash
        aws acm describe-certificate --certificate-arn "<CERTIFICATE-ARN>"
        ```
    3. Create custom domain name for `api.<YOUR-DOMAIN>`, `auth.<YOUR-DOMAIN>`, `wss.<YOUR-DOMAIN>` (repeat for each subdomain):
        ```bash
        aws apigatewayv2 create-domain-name --domain-name "api.karipid.store" --domain-name-configurations "CertificateArn=arn:aws:acm:eu-central-1:975050129031:certificate/75cecf7d-d5dc-48d8-8e70-50b4af4bc1d9,EndpointType=REGIONAL"
        ```
    4. Get your Websocket and Rest API Gateway IDs (The names are `<STAGE>-air-remote-backend-websockets` & `<STAGE>-air-remote-backend`):
        ```bash
        aws apigatewayv2 get-apis
        aws apigateway get-rest-apis
        ```
    5. Map Domains `api.`, `auth.` to Rest API (repeat for both):
        ```bash
        aws apigateway create-base-path-mapping --domain-name "<SUBDOMAIN>.<YOUR-DOMAIN>" --rest-api-id "<REST-API-ID>" --stage "prod"
        ```
    6. Map `wss.` domain to your Websocket API:
        ```bash
        aws apigatewayv2 create-api-mapping --domain-name "wss.<YOUR-DOMAIN>" --api-id "<WSS-ID>" --stage "prod" --api-mapping-key "(none)"
        ```
    7. For each of the subdomains `api.`,`auth.` and `wss.` search for `ApiGatewayDomainName` that will be in this format `d-xyz1234.execute-api.eu-central-1.amazonaws.com`, along with `HostedZoneId`:
        ```bash
        aws apigatewayv2 get-domain-name --domain-name "<SUBDOMAIN>.<YOUR-DOMAIN>"
        ```
    8. Create an Alias (A) record (replace `<ROUTE-53-HOSTED-ZONE-ID>` with the hosted zone id you can obtain using `aws route53 list-hosted-zones` and `<HOSTED-ZONE-ID>` with the one from previous step), for each of the subdomains:
        ```bash
        aws route53 change-resource-record-sets --hosted-zone-id <ROUTE-53-HOSTED-ZONE-ID> --change-batch '{
        "Changes": [
            {
                "Action": "CREATE",
                "ResourceRecordSet": {
                    "Name": "<SUBDOMAIN>.<YOUR-DOMAIN>",
                    "Type": "A",
                    "AliasTarget": {
                        "HostedZoneId": "<HOSTED-ZONE-ID>", 
                        "DNSName": "<API-GATEWAY-DOMAIN-NAME>",
                        "EvaluateTargetHealth": false
                    }
                }
            }
        ]
        }'
        ```
17. #### 🎉 You're ready.
  You can go ahead and sign up with your admin email and begin using the app!
    
---

## 📜 License
Licensed under the GPL V3.0 License.
<a href="https://github.com/jugeekuz/AirRemote-Embedded/blob/master/LICENSE">🔗 View License Details </a>


---

## 🤝 Contributing
Feel free to fork the repository and contribute! Pull requests and feedback are welcome.

24.02.26 sync fork
Ось результати аналізу проекту **AirRemote-Frontend** та стратегія його трансформації, підготовлені у форматі для копіювання в Notion.

---

# 📑 Звіт AI-консультанта: Проект "AirRemote"

**AirRemote** — це комплексне рішення для перетворення застарілих пристроїв з інфрачервоним (ІЧ) керуванням на сучасні "розумні" пристрої з дистанційним доступом.

---

## 🧬 Частина 1: "ДНК" Проекту

Логіку коду AirRemote можна розбити на такі **атомарні функції**:

*   **Авторизація та безпека:** Керування доступом користувачів до інтерфейсу та команд через захищений серверний бекенд (AWS Lambda/API Gateway).
*   **Захоплення та запис ІЧ-сигналів:** Функція зчитування інфрачервоних сигналів з існуючих фізичних пультів та їх збереження у базу даних для подальшого використання.
*   **Відтворення команд (Replay):** Передача збережених команд через веб-інтерфейс або автоматизації назад на пристрій для керування технікою.
*   **Оркестрація автоматизацій:** Створення та виконання послідовностей операцій за розкладом (наприклад, увімкнення кондиціонера за 20 хвилин до прибуття додому).
*   **Керування конфігурацією пристроїв:** CRUD-операції (створення, редагування, видалення) для віртуальних пультів та впорядкування їхніх "плиток" в інтерфейсі.
*   **Captive Portal (Ініціалізація):** Механізм надання доступу гостям або друзям та початкове налаштування облікових даних пристрою.

### 💎 Головна технічна цінність
Головна цінність AirRemote полягає в **універсальній модернізації (Legacy Modernization)**. Проект дозволяє інтегрувати будь-яку техніку (навіть рідкісну чи стару), що керується ІЧ-пультами, у сучасну екосистему "розумного дому" без втручання в апаратну частину самої техніки. Використання **Serverless архітектури** забезпечує масштабованість та економічність системи.

---

## 🚀 Частина 2: "Трансформація" (Інтеграція з Gemini LLM)

Додавання мультимодальної моделі **Gemini** (через інструменти **GitHub Models** або **GitHub Spark**) перетворює AirRemote на **інтелектуального домашнього асистента**.

### Як зміниться функціонал?
1.  **Семантичне керування:** Замість натискання кнопок користувач може вводити запити природною мовою: *"Зроби так, щоб мені було комфортно спати"*. Gemini проаналізує цей запит і сама вибере послідовність команд для кондиціонера та зволожувача повітря.
2.  **Прогностична автоматизація:** ШІ аналізуватиме ваші звички та самостійно пропонуватиме створити автоматизації на основі контексту (наприклад, погоди чи часу доби).
3.  **Візуальне розпізнавання пультів:** Використовуючи камеру телефону, Gemini може розпізнати фізичний пульт і автоматично знайти відповідні ІЧ-коди в базі даних, спрощуючи процес налаштування.

### Сценарій сервісу "Comfort-as-a-Service" (AirRemote + Gemini + ID_{$})

Сценарій створення інтелектуального сервісу на вашому сайті:
1.  **Інтерфейс (Ваш сайт):** Клієнт бачить одну кнопку "Оптимізувати клімат".
2.  **Обробка (Gemini):** Коли клієнт натискає кнопку, Gemini отримує дані про поточну температуру в кімнаті та бажаний рівень комфорту.
3.  **Логіка (ID_{$1}):** Ваш базовий Python-скрипт **ID_{$1}** перевіряє поточний стан пристроїв через API AirRemote.
4.  **Виконання (AirRemote API):** На основі рішення Gemini, скрипт **ID_{$2}** надсилає запит до бекенду AirRemote (AWS API Gateway) для відтворення потрібної ІЧ-команди.
5.  **Деплой:** Використовуючи **GitHub Spark**, ви розгортаєте цей інтелектуальний міст як веб-додаток, де AirRemote відповідає за фізичну дію, а ваші скрипти та Gemini — за інтелектуальний вибір.

---

## 📋 План дій для Notion
| Крок | Дія | Результат |
| :--- | :--- | :--- |
| **1** | Розгортання бекенду на AWS (Lambda + DynamoDB) | Робоча серверна частина |
| **2** | Хостинг фронтенду на S3 + CloudFront | Доступ до веб-панелі |
| **3** | Підключення Gemini через GitHub Models | "Мізки" для обробки запитів |
| **4** | Зв'язування з вашими скриптами `ID_{$}` | Автоматизація бізнес-логіки |

---

### 💡 Резюме

**Суть:** **Модернізація ІЧ-пристроїв через веб-інтерфейс**.

**AI-Роль:** **Створення інтелектуальних застосунків через Spark**.
