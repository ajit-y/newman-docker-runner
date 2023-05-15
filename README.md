# newman-docker-runner
Dockerfile and Docker commands to run Postman collection with Postman API for collections and environment


## USECASE
- There is a postman collection for tests to be run using newman
- There is a Postman environment created for collection
- Newman should run the tests directly using Postman API with Collection and Environment in Postman cloud
- Newman should be run using Docker

## STEPS
**Step1:**
Navigate to directory with Dockerfile and build an image using command below
```shell
docker build -t newman-runner .
```

**Step2:**

_If the Collection need to be run in a specific Postman Environment_
```text
docker run -t --rm \
-e COLLECTIONID=<ENTER COLLECTION ID HERE> \
-e POSTMANAPIKEY=<ENTER YOUR POSTMAN API KEY HERE> \
-e ENVIRONMENTID=<ENTER THE ENVIRONMENT ID HERE> \
-v ~/postman-dir:/etc/newman \
newman-runner
```

EXAMPLE:
```text
docker run -t --rm \
-e COLLECTIONID=12345678-cbcdfbcf-a7j7-40f4-b6d4-78c7efc66d98 \
-e POSTMANAPIKEY=PMAK-1234cf7f56c78e3c98765ad7-1fb1234ee8f3d6fbbc79b8b2f03d11ca1 \
-e ENVIRONMENTID=12345678-789d5c98-1432-43e8-1234-1aecf0b2f2de \
-v ~/postman-dir:/etc/newman \
newman-runner
```

_If there is no specific Postman Environment needed to run the collection_
```text
docker run -t --rm \
-e COLLECTIONID=<ENTER COLLECTION ID HERE> \
-e POSTMANAPIKEY=<ENTER YOUR POSTMAN API KEY HERE> \
-v ~/postman-dir:/etc/newman \
newman-runner
```

**Step3:**
View reports at
```text
/Users/dev/postman-dir/newman
```

## External reference

[Postman Collections](https://learning.postman.com/docs/collections/collections-overview/)

[Postman Environments](https://learning.postman.com/docs/sending-requests/managing-environments/)

[How to get Postman API Key](https://learning.postman.com/docs/developer/postman-api/authentication/#generate-a-postman-api-key)

[How to Get Id for Collection and Environment](https://support.postman.com/hc/en-us/articles/5063785095319-How-to-find-the-ID-of-an-element-in-Postman)

[Newman With Docker](https://learning.postman.com/docs/collections/using-newman-cli/newman-with-docker/)
