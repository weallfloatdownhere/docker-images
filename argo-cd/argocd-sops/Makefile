TAGS=0.1.0
DOCKERIMAGE=sops-argo-cd
IMAGE_NAME=${DOCKERUSERNAME}/${DOCKERIMAGE}

pushall:
	$(call dist)
	$(call latest)

build:
	@DOCKER_BUILDKIT=1 docker build -t ${DOCKERIMAGE} .

login:build
	@docker login --username="${DOCKERUSERNAME}" --password="${DOCKERPASSWORD}"

dist:login
	@docker tag ${DOCKERIMAGE} $(IMAGE_NAME):dist-${TAGS}
	@docker push $(IMAGE_NAME):dist-${TAGS}

tagged:login
	@docker tag ${DOCKERIMAGE} $(IMAGE_NAME):${TAGS}
	@docker push $(IMAGE_NAME):${TAGS}

latest:tagged
	@docker tag ${DOCKERIMAGE} $(IMAGE_NAME):latest
	@docker push $(IMAGE_NAME):latest