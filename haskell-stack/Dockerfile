FROM debian:bullseye

ENV STACK_VER   2.1.3
ENV LLVM_VER    8

ENV LANG        C.UTF-8
RUN apt-get update && \
    apt-get install -y --no-install-recommends llvm-${LLVM_VER} xz-utils make upx libgmp-dev file \
            zlib1g-dev libtinfo-dev libsqlite3-0 libsqlite3-dev ca-certificates g++ git curl && \
    curl -fSL https://github.com/commercialhaskell/stack/releases/download/v${STACK_VER}/stack-${STACK_VER}-linux-x86_64-static.tar.gz -o stack.tar.gz && \
    apt-get purge -y --auto-remove curl && \
    tar -xf stack.tar.gz -C /usr/local/bin --strip-components=1 && \
    rm -rf "$GNUPGHOME" /var/lib/apt/lists/* /stack.tar.gz && \
    rm -rf /usr/share/doc /usr/share/man

ENV PATH /usr/lib/llvm-${LLVM_VER}/bin/:$PATH
COPY stack-build /usr/local/bin/
RUN chmod +x /usr/local/bin/stack-build

