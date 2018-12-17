# サンプルデータ

パブリックドメインの [Natural Earth](https://www.naturalearthdata.com/) のデータを利用したサンプルデータです。

データは [1:50m Cultural Vectors Admin 0 - Countries](https://www.naturalearthdata.com/downloads/50m-cultural-vectors/50m-admin-0-countries-2/) を利用しています。

[Made with Natural Earth](https://www.naturalearthdata.com/about/terms-of-use/).

# データの入手方法

## すべて

* https://github.com/tohka/ne/archive/master.zip

## 個別

* Shapefile
  * https://raw.githubusercontent.com/tohka/ne/master/Shapefile/ne_50m_admin_0_countries.zip
* GeoJSON
  * https://raw.githubusercontent.com/tohka/ne/master/GeoJSON/ne_50m_admin_0_countries.geojson
* CSV
  * https://raw.githubusercontent.com/tohka/ne/master/CSV/ne_50m_admin_0_countries.csv
* SpatiaLite
  * https://raw.githubusercontent.com/tohka/ne/master/SpatiaLite/ne_50m_admin_0_countries.sqlite
* GeoPackage
  * https://raw.githubusercontent.com/tohka/ne/master/GeoPackage/ne_50m_admin_0_countries.gpkg

# データ作成方法

```shell-session
$ mkdir -p Shapefile GeoJSON CSV SpatiaLite GeoPackage
$ ogr2ogr -f GeoJSON ./GeoJSON/ne_50m_admin_0_countries.geojson ./ne_50m_admin_0_countries.shp
$ ogr2ogr -f CSV -lco GEOMETRY=AS_WKT -lco SEPARATOR=TAB ./CSV/ne_50m_admin_0_countries.csv ./ne_50m_admin_0_countries.shp
$ ogr2ogr -f SQLite -dsco SPATIALITE=YES -nlt PROMOTE_TO_MULTI ./SpatiaLite/ne_50m_admin_0_countries.sqlite ./ne_50m_admin_0_countries.shp
$ ogr2ogr -f GPKG ./GeoPackage/ne_50m_admin_0_countries.gpkg ./ne_50m_admin_0_countries.shp
$ mv ./ne_50m_admin_0_countries.{shp,dbf,shx,prj,cpg} ./Shapefile
```
