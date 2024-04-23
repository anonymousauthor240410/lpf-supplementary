## Run Fuzzing (Default)

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:tf
	 ```

 - Run Docker Container
	```bash
	export TARGET_API=array_ops_BroadcastTo
	export TIME_BUDGET=3600
	export OUT_DIR=$PWD/lpf_rq2_tf_default
	
	docker run --rm -it --cpus 1 -w /root/tensorflow \
	  --env LD_LIBRARY_PATH=/root/.opam/4.08.0/lib/z3 \
	  -v ${OUT_DIR}/${TARGET_API}:/root/tensorflow/experiment_result \
	  --name lpf_tensorflow anonymousauthor240410/pathfinder:tf \
	  bazel-bin/tensorflow/core/kernels/pathfinder/generated/default/pathfinder_driver_main \
	    ${TARGET_API} \
	    --max_total_time ${TIME_BUDGET} \
	    --corpus /root/tensorflow/experiment_result/corpus
	```
	* You may want to add `--verbose 1` to see how ACT grows as the fuzzing progresses.

## Measure Coverage (Default)

  - Measure Coverage
	```bash
	export TARGET_API=array_ops_BroadcastTo
	export TIME_BUDGET=3600
	export TIME_INTERVAL=300
	export OUT_DIR=$PWD/lpf_rq2_tf_default
	
	docker run --rm -it -w /root/tensorflow \
	  -v ${OUT_DIR}/${TARGET_API}:/root/tensorflow/experiment_result \
	  --name lpf_tensorflow_cov anonymousauthor240410/pathfinder:tf-cov \
	  bazel-bin/tensorflow/core/kernels/pathfinder/generated/default/pathfinder_driver_main \
	    ${TARGET_API} --run_only --ignore_exception \
	    --max_total_time ${TIME_BUDGET} \
	    --cov_interval_time ${TIME_INTERVAL} \
	    --corpus /root/tensorflow/experiment_result/corpus \
	    --output_cov /root/tensorflow/experiment_result/cov.csv
  	```

## Run Fuzzing (LPF-NDP)

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:tf
	 ```

 - Run Docker Container
	```bash
	export TARGET_API=array_ops_BroadcastTo
	export TIME_BUDGET=3600
	export OUT_DIR=$PWD/lpf_rq2_tf_ndp
	
	docker run --rm -it --cpus 1 -w /root/tensorflow \
	  --env LD_LIBRARY_PATH=/root/.opam/4.08.0/lib/z3 \
	  -v ${OUT_DIR}/${TARGET_API}:/root/tensorflow/experiment_result \
	  --name lpf_tensorflow anonymousauthor240410/pathfinder:tf \
	  bazel-bin/tensorflow/core/kernels/pathfinder/generated/default/pathfinder_driver_main \
	    ${TARGET_API} \
	    --prune_nd 0 \
	    --max_total_time ${TIME_BUDGET} \
	    --corpus /root/tensorflow/experiment_result/corpus
	```
	* You may want to add `--verbose 1` to see how ACT grows as the fuzzing progresses.

## Measure Coverage (LPF-NDP)

  - Measure Coverage
	```bash
	export TARGET_API=array_ops_BroadcastTo
	export TIME_BUDGET=3600
	export TIME_INTERVAL=300
	export OUT_DIR=$PWD/lpf_rq2_tf_ndp
	
	docker run --rm -it -w /root/tensorflow \
	  -v ${OUT_DIR}/${TARGET_API}:/root/tensorflow/experiment_result \
	  --name lpf_tensorflow_cov anonymousauthor240410/pathfinder:tf-cov \
	  bazel-bin/tensorflow/core/kernels/pathfinder/generated/default/pathfinder_driver_main \
	    ${TARGET_API} --run_only --ignore_exception \
	    --max_total_time ${TIME_BUDGET} \
	    --cov_interval_time ${TIME_INTERVAL} \
	    --corpus /root/tensorflow/experiment_result/corpus \
	    --output_cov /root/tensorflow/experiment_result/cov.csv
  	```

## Run Fuzzing (LPF-STAGED)

 - Pull Docker Image
	 ```bash
	 docker pull anonymousauthor240410/pathfinder:tf
	 ```

 - Run Docker Container
	```bash
	export TARGET_API=array_ops_BroadcastTo
	export TIME_BUDGET=3600
	export OUT_DIR=$PWD/lpf_rq2_tf_staged
	
	docker run --rm -it --cpus 1 -w /root/tensorflow \
	  --env LD_LIBRARY_PATH=/root/.opam/4.08.0/lib/z3 \
	  -v ${OUT_DIR}/${TARGET_API}:/root/tensorflow/experiment_result \
	  --name lpf_tensorflow anonymousauthor240410/pathfinder:tf \
	  bazel-bin/tensorflow/core/kernels/pathfinder/generated/single_stage/pathfinder_driver_main \
	    ${TARGET_API} \
	    --max_total_time ${TIME_BUDGET} \
	    --corpus /root/tensorflow/experiment_result/corpus
	```
	* You may want to add `--verbose 1` to see how ACT grows as the fuzzing progresses.

## Measure Coverage (LPF-STAGED)

  - Measure Coverage
	```bash
	export TARGET_API=array_ops_BroadcastTo
	export TIME_BUDGET=3600
	export TIME_INTERVAL=300
	export OUT_DIR=$PWD/lpf_rq2_tf_staged
	
	docker run --rm -it -w /root/tensorflow \
	  -v ${OUT_DIR}/${TARGET_API}:/root/tensorflow/experiment_result \
	  --name lpf_tensorflow_cov anonymousauthor240410/pathfinder:tf-cov \
	  bazel-bin/tensorflow/core/kernels/pathfinder/generated/single_stage/pathfinder_driver_main \
	    ${TARGET_API} --run_only --ignore_exception \
	    --max_total_time ${TIME_BUDGET} \
	    --cov_interval_time ${TIME_INTERVAL} \
	    --corpus /root/tensorflow/experiment_result/corpus \
	    --output_cov /root/tensorflow/experiment_result/cov.csv
  	```

## Target API List (115 APIs)

array_ops_BroadcastTo\
array_ops_DepthToSpace\
array_ops_Diag\
array_ops_DiagPart\
array_ops_EnsureShape\
array_ops_ExpandDims\
array_ops_Gather\
array_ops_GatherNd\
array_ops_Identity\
array_ops_MatrixBandPart\
array_ops_MatrixDiag\
array_ops_MatrixDiagPart\
array_ops_MatrixDiagPartV2\
array_ops_MatrixDiagPartV3\
array_ops_MatrixDiagV2\
array_ops_MatrixDiagV3\
array_ops_MatrixSetDiagV2\
array_ops_MatrixSetDiagV3\
array_ops_OnesLike\
array_ops_Pad\
array_ops_PadV2\
array_ops_Where\
array_ops_ZerosLike\
image_ops_AdjustHue\
image_ops_AdjustSaturation\
image_ops_EncodePng\
image_ops_ExtractGlimpse\
image_ops_HSVToRGB\
image_ops_ResizeBicubic\
image_ops_ResizeBilinear\
image_ops_ResizeNearestNeighbor\
image_ops_RGBToHSV\
io_ops_MatchingFiles\
math_ops_Abs\
math_ops_Add\
math_ops_AddN\
math_ops_AddV2\
math_ops_All\
math_ops_Any\
math_ops_Asin\
math_ops_Asinh\
math_ops_Atan\
math_ops_Atanh\
math_ops_Ceil\
math_ops_ClipByValue\
math_ops_ComplexAbs\
math_ops_Conj\
math_ops_Cumsum\
math_ops_Div\
math_ops_DivNoNan\
math_ops_Equal\
math_ops_Exp\
math_ops_Expm1\
math_ops_Floor\
math_ops_FloorMod\
math_ops_GreaterEqual\
math_ops_Inv\
math_ops_Less\
math_ops_LessEqual\
math_ops_Lgamma\
math_ops_Log1p\
math_ops_LogicalAnd\
math_ops_LogicalNot\
math_ops_LogicalOr\
math_ops_MatMul\
math_ops_Max\
math_ops_Mean\
math_ops_Min\
math_ops_Minimum\
math_ops_Mod\
math_ops_MulNoNan\
math_ops_NotEqual\
math_ops_Pow\
math_ops_Prod\
math_ops_RealDiv\
math_ops_Reciprocal\
math_ops_Rint\
math_ops_Round\
math_ops_Rsqrt\
math_ops_SegmentMax\
math_ops_SegmentMean\
math_ops_SelectV2\
math_ops_Sigmoid\
math_ops_Sign\
math_ops_Sin\
math_ops_Sinh\
math_ops_SparseMatMul\
math_ops_Sqrt\
math_ops_Square\
math_ops_Sum\
math_ops_Tan\
math_ops_Tanh\
math_ops_TruncateDiv\
math_ops_TruncateMod\
math_ops_Xdivy\
math_ops_Xlog1py\
math_ops_Xlogy\
nn_ops_BiasAdd\
nn_ops_Elu\
nn_ops_LogSoftmax\
nn_ops_NthElement\
nn_ops_Relu\
nn_ops_Relu6\
nn_ops_Softmax\
nn_ops_Softplus\
nn_ops_Softsign\
parsing_ops_SerializeTensor\
random_ops_Multinomial\
random_ops_RandomUniformInt\
string_ops_AsString\
string_ops_RegexReplace\
string_ops_StringLength\
string_ops_StringLower\
string_ops_StringUpper\
string_ops_UnicodeScript
