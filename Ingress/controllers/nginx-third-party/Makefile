all: push

# 0.0 shouldn't clobber any release builds
TAG = 0.1
PREFIX = aledbf/nginx-third-party

controller: controller.go clean
	CGO_ENABLED=0 GOOS=linux godep go build -a -installsuffix cgo -ldflags '-w' -o nginx-third-party-lb

container: controller
	docker build -t $(PREFIX):$(TAG) .

push: container
	gcloud docker push $(PREFIX):$(TAG)

clean:
	rm -f nginx-third-party-lb
