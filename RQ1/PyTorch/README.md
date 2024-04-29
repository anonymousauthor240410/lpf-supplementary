## Run Fuzzing

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:torch
	 ```

 - Run Docker Container
	```bash
	export TARGET_API=torch_nn_functional_adaptive_avg_pool1d
	export TIME_BUDGET=3600
	export OUT_DIR=$PWD/lpf_rq1_torch
	
	docker run --rm -it --cpus 1 -w /root/pytorch \
	  --env LD_LIBRARY_PATH=/root/.opam/4.08.0/lib/z3 \
	  -v ${OUT_DIR}/${TARGET_API}:/root/pytorch/experiment_result \
	  --name lpf_torch anonymousauthor240410/pathfinder:torch \
	  /root/pytorch/build/bin/lpf_fuzz_driver_default_${TARGET_API} \
	    --max_total_time ${TIME_BUDGET} \
	    --corpus /root/pytorch/experiment_result/corpus
	```
	* You may want to add `--verbose 1` to see how ACT grows as the fuzzing progresses.

## Measure Coverage

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:torch-cov
	 ```

  - Measure Coverage
	```bash
	export TARGET_API=torch_nn_functional_adaptive_avg_pool1d
	export TIME_BUDGET=3600
	export TIME_INTERVAL=300
	export OUT_DIR=$PWD/lpf_rq1_torch
	
	docker run --rm -it -w /root/pytorch \
	  -v ${OUT_DIR}/${TARGET_API}:/root/pytorch/experiment_result \
	  --name lpf_torch_cov anonymousauthor240410/pathfinder:torch-cov \
	  /root/pytorch/build/bin/lpf_fuzz_driver_default_${TARGET_API} \
	    --run_only --ignore_exception \
	    --max_total_time ${TIME_BUDGET} \
	    --cov_interval_time ${TIME_INTERVAL} \
	    --corpus /root/pytorch/experiment_result/corpus \
	    --output_cov /root/pytorch/experiment_result/cov.csv
  	```
    - Coverage result will be written to `${OUT_DIR}/${TARGET_API}/cov.csv`.

## Target API List (57 APIs)

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
