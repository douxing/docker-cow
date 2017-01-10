FROM alpine:3.4

# in China mainland, use mirrors from ustc
# @see http://mirrors.ustc.edu.cn/

RUN set -ex \
  && echo -e "http://mirrors.ustc.edu.cn/alpine/v3.4/main\nhttp://mirrors.ustc.edu.cn/alpine/v3.4/community" > /etc/apk/repositories \
  && mkdir -p /root/go/src \
  && export GOPATH="/root/go" \
  && apk add -v --progress --no-cache --virtual .build-deps git go \
  && git clone --progress https://github.com/cyfdecyf/bufio.git /root/go/src/github.com/cyfdecyf/bufio \
  && git clone --progress https://github.com/cyfdecyf/color.git /root/go/src/github.com/cyfdecyf/color \
  && git clone --progress --branch 0.9.8 https://github.com/cyfdecyf/cow.git /root/go/src/github.com/cyfdecyf/cow \
  && git clone --progress https://github.com/cyfdecyf/leakybuf.git /root/go/src/github.com/cyfdecyf/leakybuf \
  && git clone --progress https://github.com/codahale/chacha20.git /root/go/src/github.com/codahale/chacha20 \
  && git clone --progress https://github.com/shadowsocks/shadowsocks-go.git /root/go/src/github.com/shadowsocks/shadowsocks-go \
  && git clone --progress https://github.com/golang/crypto.git /root/go/src/golang.org/x/crypto \
  && cd /root/go/src/github.com/cyfdecyf/cow \
  && go build -o /usr/local/bin/cow \
  && apk del .build-deps \
  && unset GOPATH \
  && rm -rf /root/go

WORKDIR /root/.cow

CMD [ "cow" ]
