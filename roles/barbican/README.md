# Barbican role

- docker-engine needs to be intalled on the remote host.
- `pip install docker docker-compose`

## Test

```shell
PREFIX=http://127.0.0.1:9311/v1
http get $PREFIX/secrets X-Project-Id:123
cat <<EOF | http post $PREFIX/secrets X-Project-Id:123
{
  "name": "my-secret",
    "payload": "i won't tell you",
    "payload_content_type": "text/plain"
}
EOF
http get $PREFIX/secrets/4e90ca8c-0f08-4ed9-abe5-267eeb95c479/payload X-Project-Id:123
```