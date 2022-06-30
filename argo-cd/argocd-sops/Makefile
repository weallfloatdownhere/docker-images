TAGS=0.1.0
DOCKERIMAGE=sops-argo-cd
IMAGE_NAME=${DOCKERUSERNAME}/$(DOCKERIMAGE)

build:
	DOCKER_BUILDKIT=1 docker build -t $(DOCKERIMAGE) .

login:build
	@docker login --username="${DOCKERUSERNAME}" --password="${DOCKERPASSWORD}"

dist:login
	@docker tag -t $(DOCKERIMAGE) $(IMAGE_NAME):dist-$(TAGS)
	@docker push $(IMAGE_NAME):dist-$(TAGS)

tagged:login
	@docker tag -t $(DOCKERIMAGE) $(IMAGE_NAME):$(TAGS)
	@docker push $(IMAGE_NAME):$(TAGS)

latest:tagged
	@docker tag -t $(DOCKERIMAGE) $(IMAGE_NAME):latest
	@docker push $(IMAGE_NAME):latest
  
pushall:
  make latest
  make dist
