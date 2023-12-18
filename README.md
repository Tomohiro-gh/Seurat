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


## metadataの追加：既存のmetaを参考にして新たに追加するversion
```r
ECatlasQC@meta.data <- 
  ECatlasQC@meta.data %>% 
  mutate(rough_annotation =
           case_when(Cluster %in% A ~ 'Artery',
                     Cluster %in% V ~ 'Vein',
                     Cluster %in% C ~ 'Capillary',
                     Cluster %in% M ~ 'Mitotic',
                     Cluster %in% An ~ 'Angiogenic',
                     Cluster %in% L ~ 'Lymphatic'))


#また，一部のみを変更し，以下は同様としたい場合は， # TRUE ~ で指定する
SeuratObj@metadata <-
  SeuratObj@metadata %>% 
  mutate(
    Modified_MCannotation =
      case_when(rownames(AnnotationData) %in% Barcode_SMC ~ 'SMC',
                TRUE ~ Author_Annotation))

```
