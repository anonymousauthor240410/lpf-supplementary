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

## Covered API List (000 APIs)

torch_nn_functional_adaptive_avg_pool1d\
torch_nn_functional_adaptive_avg_pool2d\
torch_nn_functional_adaptive_avg_pool3d\
torch_nn_functional_adaptive_max_pool2d\
torch_nn_functional_avg_pool1d\
torch_nn_functional_avg_pool2d\
torch_nn_functional_batch_norm\
torch_nn_functional_binary_cross_entropy\
torch_nn_functional_binary_cross_entropy_with_logits\
torch_nn_functional_celu\
torch_nn_functional_conv1d\
torch_nn_functional_conv2d\
torch_nn_functional_conv3d\
torch_nn_functional_conv_transpose2d\
torch_nn_functional_cosine_similarity\
torch_nn_functional_cross_entropy\
torch_nn_functional_dropout\
torch_nn_functional_dropout3d\
torch_nn_functional_embedding\
torch_nn_functional_gelu\
torch_nn_functional_hardshrink\
torch_nn_functional_hardtanh\
torch_nn_functional_hinge_embedding_loss\
torch_nn_functional_huber_loss\
torch_nn_functional_instance_norm\
torch_nn_functional_interpolate\
torch_nn_functional_kl_div\
torch_nn_functional_layer_norm\
torch_nn_functional_local_response_norm\
torch_nn_functional_log_softmax\
torch_nn_functional_logsigmoid\
torch_nn_functional_lp_pool1d\
torch_nn_functional_lp_pool2d\
torch_nn_functional_margin_ranking_loss\
torch_nn_functional_max_pool1d\
torch_nn_functional_max_pool2d\
torch_nn_functional_max_unpool3d\
torch_nn_functional_mish\
torch_nn_functional_multilabel_soft_margin_loss\
torch_nn_functional_nll_loss\
torch_nn_functional_pad\
torch_nn_functional_pairwise_distance\
torch_nn_functional_pixel_unshuffle\
torch_nn_functional_poisson_nll_loss\
torch_nn_functional_prelu\
torch_nn_functional_relu\
torch_nn_functional_relu6\
torch_nn_functional_selu\
torch_nn_functional_silu\
torch_nn_functional_smooth_l1_loss\
torch_nn_functional_soft_margin_loss\
torch_nn_functional_softmax\
torch_nn_functional_softplus\
torch_nn_functional_tanhshrink\
torch_nn_functional_threshold\
torch_nn_functional_triplet_margin_loss\
torch_nn_functional_triplet_margin_with_distance_loss
