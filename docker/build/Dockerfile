FROM centos:7
MAINTAINER "Tom" <tom_hejiaxi@163.com>

ENV PATH=$PATH:/usr/local/node/bin
ENV BLOG_DIR="/var/www/blog"
ARG username
ARG useremail

RUN yum install -y git-core \
    && curl -sL https://rpm.nodesource.com/setup_13.x | bash - \
    && yum install -y nodejs \
    && npm install -g hexo@5.4.0 \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && hexo init $BLOG_DIR \
    && cd $BLOG_DIR \
    && npm install hexo-deployer-git --save \
    && npm install hexo-excerpt --save \
    && npm install hexo-word-counter --save \
    && npm install hexo-optimize --save \
    && npm install hexo-generator-searchdb --save

RUN cd $BLOG_DIR \
    && git clone --branch v8.5.0 https://github.com/hexo-theme-next/hexo-theme-next themes/next


WORKDIR $BLOG_DIR