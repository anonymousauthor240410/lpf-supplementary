## How to Run Fuzz Driver Generator

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:tf
	 ```

 - Init Container
	```bash
	export OUT_DIR=$PWD/lpf_fuzz_drivers_tf

	docker run -itd -w /root/tensorflow/lpf_fuzz_driver_generator \
	  -v ${OUT_DIR}:/root/lpf_fuzz_drivers_tf \
	  --name lpf_fdg_tf anonymousauthor240410/pathfinder:tf
	docker exec -it lpf_fdg_tf bash
	```

 - Build Fuzz Driver Generator
	```bash
	bazel build pdg
	```

 - Generate Fuzz Drivers
	```bash
	cd /root && cd lpf_fuzz_drivers_tf
	/root/tensorflow/bazel-bin/lpf_fuzz_driver_generator/pdg
	exit
	```

 - Terminate Container
	```bash
	docker rm -f lpf_fdg_tf
	```
	