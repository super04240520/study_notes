post api
```curl 'https://geo-tools-apigw.stg.mngd.int.engtools.net/api/v2/user_group' \
  -H 'accept: application/json, text/plain, */*' \
  -H 'accept-language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7' \
  -H 'authorization: eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJnZW9fdG9vbHMiLCJjb25jZWRvX2lkIjoiMTBiOTk2ZGMwMTI5NGY1NjliZjlmZmMzOTViOGI3ZjIiLCJleHAiOjE3MTM4NDk3NTksImlzcyI6InN0Zy1jb25jZWRvLWlhbSIsImp0aSI6ImQwMDkyYTgxZDkwNDRmZmJhNDk1MDY5M2QwY2Q3YzQ3IiwibmFtZSI6ImNoYW5nbGluLnNoaUBncmFidGF4aS5jb20iLCJzdWIiOiJjaGFuZ2xpbi5zaGlAZ3JhYnRheGkuY29tIiwic3ViamVjdF9hdHRyaWJ1dGVzIjp7ImJhc2ljX2F0dHJpYnV0ZXMiOnsiQ29uY2Vkb0lEIjoiMTBiOTk2ZGMwMTI5NGY1NjliZjlmZmMzOTViOGI3ZjIiLCJFbWFpbCI6ImNoYW5nbGluLnNoaUBncmFidGF4aS5jb20iLCJFbXBsb3llZUlEIjoiIiwiU3VwZXJ2aXNvcnlPcmciOiIiLCJTdXBlcnZpc29yeU9yZ0lEIjoiIiwiV29ya2VyVHlwZSI6IiIsIldvcmtlclN1YlR5cGUiOiIiLCJNYW5hZ2VyRW1haWwiOiIiLCJNYW5hZ2VySUQiOiIiLCJDb3VudHJ5IjoiIiwiTG9jYXRpb24iOiIiLCJMb2NhdGlvbklEIjoiIiwiRGVwYXJ0bWVudCI6IiIsIlZlcnRpY2FsIjoiIiwiVmVydGljYWxDb2RlIjoiIiwiQ29zdENlbnRlciI6IiIsIkNvc3RDZW50ZXJDb2RlIjoiIiwiUHJvZHVjdCI6IiIsIlByb2R1Y3RDb2RlIjoiIiwiSm9iRmFtaWx5IjoiIiwiSm9iRmFtaWx5R3JvdXAiOiIiLCJKb2JGYW1pbHlJRCI6IiIsIkpvYkZhbWlseUdyb3VwSUQiOiIiLCJEZXBhcnRtZW50SUQiOiIiLCJDb21wYW55IjoiIiwiQ29tcGFueUlEIjoiIiwiSm9iUHJvZmlsZSI6IiIsIkpvYlByb2ZpbGVDb2RlIjoiIiwiRGl2aXNpb24iOiIiLCJEaXZpc2lvblJlZklEIjoiIiwiU3ViVGVhbSI6IiIsIlN1YlRlYW1Db2RlIjoiIiwiU3ViTG9jYXRpb25OYW1lIjoiIiwiU3ViTG9jYXRpb25Db2RlIjoiIiwiQ29tcGVuc2F0aW9uR3JhZGUiOiIiLCJSb2xlcyI6e30sIlN1cGVydmlzb3J5T3JnQ2hhaW4iOnt9fSwiY3VzdG9tX2F0dHJpYnV0ZXMiOm51bGx9LCJ0b2tlbl90eXBlIjoiQmVhcmVyIn0.kr_3MsRvZoPKWk5dvFm9JUVrzo3qgINGuiEGH4daFOdjE1bVOS54qBj0FlXBn-AJc18llbYFg9i7aP4hl7nLxXhJMo8N-m6SU7IxOthyGWdYmRIiBqQHsVQx8yOa_Si38b86dIGhM2THzVRFQvhy3CnWK5PwjxdrLZotTo9HU4OhVEHFfrqriySXHISEs2ggxL54gyDQQ6kVzWn2SIP_uROWWw4xJ0G27x-FNvVZ9Dp1RsuwZQT0lPn8F55jm0FWglV9V3ZrB_kcpTqJ_pmhHHKFv4Z9HL_GFOUn1fcoeuUxAHrrqndwflGchgQlujJGLpJYu83BaJSGypXUqFaT_Q' \
  -H 'content-type: application/json; charset=UTF-8' \
  -H 'geo-tools-params: {"client_version":"11.0.8848720"}' \
  -H 'origin: https://geo-tools.stg-myteksi.com' \
  -H 'priority: u=1, i' \
  -H 'referer: https://geo-tools.stg-myteksi.com/' \
  -H 'sec-ch-ua: "Chromium";v="124", "Google Chrome";v="124", "Not-A.Brand";v="99"' \
  -H 'sec-ch-ua-mobile: ?0' \
  -H 'sec-ch-ua-platform: "macOS"' \
  -H 'sec-fetch-dest: empty' \
  -H 'sec-fetch-mode: cors' \
  -H 'sec-fetch-site: cross-site' \
  -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124.0.0.0 Safari/537.36' \
  -H 'x-app-identity: geo_tools' \
  -H 'x-auth-method: concedo' \
  --data-raw '{"user_id":11356,"email":"changlin.shi@grabtaxi.com","group_id":3,"msg_id":"d4e28153-0fb8-4fa7-aa8e-2a1f66277a98"}'

```
