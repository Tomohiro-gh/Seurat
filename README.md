# Seurat
Seuratのエラーなどメモしておく

```r
## error message

## Converting this matrix to Seurat object #4515
## https://github.com/satijalab/seurat/issues/4515

Error: Please run UpdateSeuratObject on your object
Error during wrapup: no slot of name "images" for this object of class "Seurat"
Error: no more error handlers available (recursive errors?); invoking 'abort' restart

```
Solution:
```r
  seurat_obj <- UpdateSeuratObject(seurat_obj)
```
