# Please choose from the below set of Docker commands to complete your Dockerfile:

# COPY
# RUN
# ADD
# EXPOSE
# FROM
# CMD
# PUSH
# PULL
# WORKDIR


FROM golang:1.15 as builder
RUN go get github.com/codegangsta/negroni

#MY CODE
RUN go get github.com/gorilla/mux github.com/xyproto/simpleredis

COPY main.go .
RUN go build main.go

FROM ubuntu:18.04

#MY CODE
COPY --from=builder /go//main /app/guestbook
COPY public/index.html /app/public/index.html
COPY public/script.js /app/public/script.js
COPY public/style.css /app/public/style.css
COPY public/jquery.min.js /app/public/jquery.min.js
#

WORKDIR /app
CMD ["./guestbook"]

#MY CODE
RUN -p 3000

export MY_NAMESPACE=sn-labs-$USERNAME

docker build . -t us.icr.io/$MY_NAMESPACE/guestbook:v1
#
