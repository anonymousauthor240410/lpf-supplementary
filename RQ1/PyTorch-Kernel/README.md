## Run Fuzzing

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:torch-kernel
	 ```

 - Run Docker Container
	```bash
	export TARGET_KERNEL_FUNC=at_native_expand
	export TIME_BUDGET=3600
	export OUT_DIR=$PWD/lpf_rq1_torch_kernel
	
	docker run --rm -it --cpus 1 -w /root/pytorch \
	  --env LD_LIBRARY_PATH=/root/.opam/4.08.0/lib/z3 \
	  -v ${OUT_DIR}/${TARGET_KERNEL_FUNC}:/root/pytorch/experiment_result \
	  --name lpf_torch_kernel anonymousauthor240410/pathfinder:torch-kernel \
	  /root/pytorch/build/bin/lpf_fuzz_driver_${TARGET_KERNEL_FUNC} \
	    --max_total_time ${TIME_BUDGET} \
	    --corpus /root/pytorch/experiment_result/corpus
	```
	* You may want to add `--verbose 1` to see how ACT grows as the fuzzing progresses.

## Measure Coverage

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:torch-kernel-cov
	 ```

  - Measure Coverage
	```bash
	export TARGET_API=at_native_expand
	export TIME_BUDGET=3600
	export TIME_INTERVAL=300
	export OUT_DIR=$PWD/lpf_rq1_torch_kernel
	
	docker run --rm -it -w /root/pytorch \
	  -v ${OUT_DIR}/${TARGET_KERNEL_FUNC}:/root/pytorch/experiment_result \
	  --name lpf_torch_kernel_cov anonymousauthor240410/pathfinder:torch-kernel-cov \
	  /root/pytorch/build/bin/lpf_fuzz_driver_${TARGET_KERNEL_FUNC} \
	    --run_only --ignore_exception \
	    --max_total_time ${TIME_BUDGET} \
	    --cov_interval_time ${TIME_INTERVAL} \
	    --corpus /root/pytorch/experiment_result/corpus \
	    --output_cov /root/pytorch/experiment_result/cov.csv
  	```

## Target Kernel Function List (78 functions)

at_native_expand\
at_native_reshape\
at_native_unbind\
at_native_select\
at_native_amax\
at_native_amin\
at_native_divide\
at_native_subtract\
at_native_isclose\
at_native_mul\
at_native_add\
at_native_rsub\
at_native_narrow\
at_native_view\
at_native_unsqueeze\
at_native_celu\
at_native_div\
at_native_permute\
at_native_split\
at_native_flatten\
at_native_dot\
at_native_allclose\
at_native_clamp_min\
at_native_logical_or\
at_native_matmul\
at_native_mv\
at_native_std\
at_native_kthvalue\
at_native_split_with_sizes\
at_native_dropout\
at_native_pdist\
at_native_add_out_sparse_cpu\
at_native_sort_cpu\
at_native_sort_cpu_stable\
at_native_kl_div\
at_native_unfold\
at_native_expand_as\
at_native_linear\
at_native_mse_loss\
at_native_sub\
at_native_repeat_interleave\
at_native_repeat_interleave_cpu\
at_native__has_compatible_shallow_copy_type\
at_native_unsafe_split\
at_native_cosine_similarity\
at_native_embedding\
at_native_constant_pad_nd\
at_native__pack_padded_sequence\
at_native_hardtanh\
at_native_type_as\
at_native_outer\
at_native_ger\
at_native_add_relu\
at_native_view_as\
at_native_alpha_dropout\
at_native_binary_cross_entropy_cpu\
at_native_feature_alpha_dropout\
at_native_reshape_as\
at_native_hinge_embedding_loss\
at_native_huber_loss\
at_native__unpack_dual\
at_native_mul_zerotensor\
at_native_add_zerotensor\
at_native_l1_loss\
at_native_multilabel_margin_loss\
at_native_prelu_cpu\
at_native_pairwise_distance\
at_native_pixel_shuffle\
at_native_pixel_unshuffle\
at_native_poisson_nll_loss\
at_native_unsafe_split_with_sizes\
at_native_soft_margin_loss\
at_native_bilinear\
at_native_grid_sampler\
at_native_norm_except_dim\
at_native_feature_dropout\
at_native_count_nonzero\
at_native_count_nonzero_cpu
