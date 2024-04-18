TODO: Upload Covered API List

## How to Run Fuzz Driver Generator

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:torch
	 ```

 - Init Container
	```bash
	export OUT_DIR=$PWD/lpf_fuzz_drivers_torch

	docker run -itd -w /root/llvm-project \
	  -v ${OUT_DIR}:/root/lpf_fuzz_drivers_torch \
	  --name lpf_fdg_torch anonymousauthor240410/pathfinder:torch
	docker exec -it lpf_fdg_torch bash
	```

 - Build Fuzz Driver Generator
	```bash
	mkdir build && cd build
	CC=clang-12 CXX=clang++-12 cmake -G Ninja \
	  -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra" -DCMAKE_INSTALL_PREFIX=. \
	  -DCMAKE_BUILD_TYPE=Debug ../llvm
	ninja
	```

 - Generate Fuzz Drivers
	```bash
	cd /root && cd lpf_fuzz_drivers_torch
	/root/llvm-project/build/bin/pathfinder-gen \
	  -p /root/pytorch/build \
	  /root/pytorch/torch/csrc/api/include/torch/torch.h
	exit
	```

 - Terminate Container
	```bash
	docker rm -f lpf_fdg_torch
	```
