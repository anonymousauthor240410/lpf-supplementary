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

## Target API List (75 APIs)

array_ops_BroadcastTo
array_ops_DepthToSpace
array_ops_DiagPart
array_ops_ExpandDims
array_ops_Gather
array_ops_GatherNd
array_ops_MatrixBandPart
array_ops_MatrixDiag
array_ops_MatrixDiagPartV2
array_ops_MatrixDiagPartV3
array_ops_MatrixDiagV2
array_ops_Pad
array_ops_Where
array_ops_ZerosLike
image_ops_AdjustSaturation
image_ops_ExtractGlimpse
image_ops_HSVToRGB
image_ops_RGBToHSV
image_ops_ResizeBicubic
image_ops_ResizeBilinear
image_ops_ResizeNearestNeighbor
math_ops_Abs
math_ops_AddV2
math_ops_All
math_ops_Asin
math_ops_Asinh
math_ops_Atan
math_ops_Atanh
math_ops_ComplexAbs
math_ops_Cumsum
math_ops_Div
math_ops_Exp
math_ops_Expm1
math_ops_Floor
math_ops_FloorMod
math_ops_Inv
math_ops_LessEqual
math_ops_Lgamma
math_ops_LogicalAnd
math_ops_LogicalOr
math_ops_MatMul
math_ops_Max
math_ops_Mean
math_ops_Mod
math_ops_MulNoNan
math_ops_Pow
math_ops_Prod
math_ops_RealDiv
math_ops_Reciprocal
math_ops_Round
math_ops_Rsqrt
math_ops_SegmentMax
math_ops_SegmentMean
math_ops_SelectV2
math_ops_Sigmoid
math_ops_Sign
math_ops_Sin
math_ops_Sinh
math_ops_SparseMatMul
math_ops_Sum
math_ops_Tanh
math_ops_TruncateDiv
math_ops_TruncateMod
math_ops_Xdivy
math_ops_Xlog1py
