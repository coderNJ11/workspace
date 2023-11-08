.PHONY: run_website install_kind create_kind_cluster install_kind create_docker_registry create_kind_cluster_with_registry connect_registry_to_kind \
	connect_registry_to_kind

run_website:
	docker build -t explorecalifornia.com . && \
		docker run --rm --name explorecalifornia.com -p 5000:80 explorecalifornia.com


stop_webiste:
	docker stop explorecalifornia.com


install_kind:
	curl --location --output kind https://github.com/kubernetes-sigs/kind/releases/download/v0.20.0/kind-darwin-amd64 &&\
		kind --version


create_kind_cluster: install_kind
	kind create cluster --name explorecalirfornia.com --config kind_config.yaml  && \
		kubectl get nodes

install_kubectl:
	brew install kubectl

create_docker_registry:
	if docker ps | grep -q 'local-registry'; \
	then echo "---> local.registry already created; skipping"
	else docker run --name local-registry -d -restart=always -p 5000:5000 registry:2; \
	fi


connect_registry_to_kind_neywork:
	docker network connect kind local-registry || true

connect_registry_to_kind: connect_registry_to_kind_neywork
	kubectl apply -f kind_config.yaml

create_kind_cluster_with_registry:
	$(MAKE) create_kind_cluster && $(MAKE) connect_registry_to_kind