# Seurat
### Seuratのエラーなどメモしておく

## Install
```r
remotes::install_github("satijalab/seurat", "seurat5", quiet = TRUE)
```


## version管理
#### check version of seurat
```r
## check suerat version
packageVersion("Seurat")
## checke object version
Version(pbmc_small)
```

## ロードしたオブジェクトのエラー
```r
## Error: Please run UpdateSeuratObject on your object
## Error during wrapup: no slot of name "images" for this object of class "Seurat"
## Error: no more error handlers available (recursive errors?); invoking 'abort' restart
```
Solution:
Converting this matrix to Seurat object #4515
https://github.com/satijalab/seurat/issues/4515
```r
  seurat_obj <- UpdateSeuratObject(seurat_obj)
```
