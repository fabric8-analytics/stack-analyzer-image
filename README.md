# f8a-sa-image
Source code for generating the docker image that initiates stack analysis for a volume mounted code repository and writes the result in a file `response.json` in the same repository. Currently, running this image can analyze NPM and PYPI application stacks.

## Build

```
git clone https://github.com/fabric8-analytics/stack-analyzer-image
cd stack-analyzer-image
docker build -t <docker user>/<image name> .
docker push <docker user>/<image name>
```
Example:
```
docker build -t mine/f8a-sa-image .
```

## Run

```
export API_GATEWAY_URL=<api-gateway-url>
export API_GATEWAY_USER_KEY=<api-gateway-user-key>
docker run -v <repo location>:/coreapi/repo -e API_GATEWAY_URL=$API_GATEWAY_URL -e API_GATEWAY_USER_KEY=$API_GATEWAY_USER_KEY <docker user>/<image name>
```
Example:
```
docker run -v /Users/samuzzal/Archive/test_repos/chalk:/coreapi/repo -e API_GATEWAY_URL='api-244530.gw.apicast.io:443/' -e API_GATEWAY_USER_KEY='5adbfd58d' mine/f8a-sa-image```
```
