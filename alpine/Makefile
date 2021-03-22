ROOT_DOCKER_IMAGE_NAME ?= libp2p-webrtc-star-service
ROOT_DOCKER_IMAGE_TAG = 0.0.1
ROOT_DOCKER_CONTAINER_NAME = star-signal

env:
	@echo "== start show env =="
	docker version
	@echo ""
	@echo "ROOT_DOCKER_IMAGE_NAME: $(ROOT_DOCKER_IMAGE_NAME)"
	@echo "ROOT_DOCKER_IMAGE_TAG: $(ROOT_DOCKER_IMAGE_TAG)"
	@echo "ROOT_DOCKER_CONTAINER_NAME: $(ROOT_DOCKER_CONTAINER_NAME)"
	@echo "==  end show env =="

imageBuild:
	docker build --tag $(ROOT_DOCKER_IMAGE_NAME):$(ROOT_DOCKER_IMAGE_TAG) .

imageRemove:
	-docker image rm -f $(ROOT_DOCKER_IMAGE_NAME):$(ROOT_DOCKER_IMAGE_TAG)

imageRebuild: imageRemove imageBuild
	@echo "rebuild $(ROOT_DOCKER_IMAGE_NAME):$(ROOT_DOCKER_IMAGE_TAG) finish"

devCreate:
	docker create --name $(ROOT_DOCKER_CONTAINER_NAME) $(ROOT_DOCKER_IMAGE_NAME):$(ROOT_DOCKER_IMAGE_TAG)

devRun: devCreate
	docker start $(ROOT_DOCKER_CONTAINER_NAME)

devLog:
	docker logs -f $(ROOT_DOCKER_CONTAINER_NAME)

devRemove:
	-docker stop $(ROOT_DOCKER_CONTAINER_NAME)
	-docker rm $(ROOT_DOCKER_CONTAINER_NAME)

fullRemove: devRemove imageRemove
	@echo "finish full remove"

fullTest: devRemove imageRebuild devRun devLog
	@echo "finish full run"

help:
	@echo "build docker at local"
	@echo "build image as: $(ROOT_DOCKER_IMAGE_NAME):$(ROOT_DOCKER_IMAGE_TAG)"
	@echo ""
	@echo "$$ make env                 ~> show  build env"
	@echo "$$ make imageBuild          ~> build image"
	@echo "$$ make imageRemove         ~> remove build image"
	@echo "$$ make imageRebuild        ~> remove and build image"
	@echo "$$ make devCreate           ~> dev mode create container"
	@echo "$$ make devRun              ~> dev mode run container"
	@echo "$$ make devLog              ~> dev mode container logs -f"
	@echo "$$ make devRemove           ~> dev mode container rm"
	@echo "$$ make fullRemove          ~> do task as: devRemove imageRemove"
	@echo "$$ make fullTest            ~> do task as: devRemove imageRebuild devRun devLog"