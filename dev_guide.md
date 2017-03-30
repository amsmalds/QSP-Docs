
QSP ditulis dengan menggunakan [JSON](https://en.wikipedia.org/wiki/JSON "JSON - Wikipedia"). Dimana JSON tersebut berisikan pemetaan HTML DOM yang akan di ambil sesuai dengan konfigurasi pada JSON tersebut.


### Skills Requirement
- Web Development (Middle)
- Mengerti CSS Selector

### Tools
- Text Editor (Notepad++, Sublime Text, dll)
- JSON Validator (Sublime Pretty JSON, dll)


### Format QSP


##### Content Parameter

| Parameter                                          | Required | Param Type      | Req. Output | Def. Output |
|----------------------------------------------------|----------|-----------------|-------------|---------|
| `name`                                             | Yes      | `String`        | -           |         |
| `base_url`                                         | Yes      | `Array`         | -           |         |
| `update_date`                                      | Yes      | `String`        | -           |         |
| `author`                                           | Optional | `String`        | -           |         |
| `author_url`                                       | Optional | `String`        | -           |         |
| `patterns`                                         | Yes      | `Object`        | -           |         |
| &nbsp; &rdsh; `list`                               | Yes      | `Object`        | -           |         |
| &nbsp; &nbsp; &nbsp; &rdsh; `pagination_url_param` | Yes      | `String`        | -           |         |
| &nbsp; &nbsp; &nbsp; &rdsh; `selector`             | Yes      | `String`        | -           |         |
| &nbsp; &nbsp; &nbsp; &rdsh; `url`                  | Yes      | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `name`                 | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `thumbnail`            | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &rdsh; `detail`                             | Yes      | `Object`        | -           |         |
| &nbsp; &nbsp; &nbsp; &rdsh; `url`                  | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `name`                 | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `price`                | Optional | [`Object:field`](#parameter-type-object-field-)  | `Integer`   | `0`     |
| &nbsp; &nbsp; &nbsp; &rdsh; `thumbnails`           | Optional | [`Object:field`](#parameter-type-object-field-)  | `Array`     | `[]`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `description`          | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `description_html`     | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `weight`               | Optional | [`Object:field`](#parameter-type-object-field-)  | `Integer`   | `0`     |
| &nbsp; &nbsp; &nbsp; &rdsh; `condition`            | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `min_order`            | Optional | [`Object:field`](#parameter-type-object-field-)  | `Integer`   | `1`     |
| &nbsp; &nbsp; &nbsp; &rdsh; `cat_1`                | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `cat_2`                | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `cat_3`                | Optional | [`Object:field`](#parameter-type-object-field-)  | `String`    | `""`    |
| &nbsp; &nbsp; &nbsp; &rdsh; `sold`                 | Optional | [`Object:field`](#parameter-type-object-field-)  | `Integer`   | `0`     |
| &nbsp; &nbsp; &nbsp; &rdsh; `views`                | Optional | [`Object:field`](#parameter-type-object-field-)  | `Integer`   | `0`     |
| &nbsp; &nbsp; &nbsp; &rdsh; `rating`               | Optional | [`Object:field`](#parameter-type-object-field-)  | `Float`     | `0.0`   |
| &nbsp; &nbsp; &nbsp; &rdsh; `rating_by`            | Optional | [`Object:field`](#parameter-type-object-field-)  | `Integer`   | `0`     |
| &nbsp; &nbsp; &nbsp; &rdsh; `__alternate`          | Optional | `Array`         | -           | `0`     |


##### Parameter Type: `Object:field`

| Param                                 | Required  | Param Type               | Note |
|---------------------------------------|-----------|---------------------------|------|
| `force_value`                         | Opitional | `String`                  | Pemaksaam hasil output. Apabila parameter ini diisi, maka CSS Selector akan diabaikan |
| `selector`                            | Opitional | `String`                  | CSS Selector |
| `exclude_selector`                    | Opitional | `Array`                   | Array CSS Selector yang di exclude |
| `read`                                | Opitional | [`String:read`](#parameter-type-string-read-)             | - |
| `temp_type_data`                      | Opitional | `String`                  | `"float"`, `"str"`, atau `"int"` |
| `output_condition`                    | Opitional | [`Object:output_condition`](#parameter-type-object-output_condition-) | - |
| `output_filter`                       | Opitional | [`Array:output_filter`](#parameter-type-array-output_filter-)     | - |

##### Parameter Type: `String:read`

Data yang dibaca dari element yang didapatkan oleh CSS Selector

- `"content"` : Membaca Content(text) di dalam CSS Selector
- `"attr:attribute_name"` : Membaca Attribute dari CSS Selector, Ganti `attribute_name` dengan nama attribue yang akan dibaca

##### Parameter Type: `Object:output_condition`

- `"fold"` : Digunakan untuk mengalikan value. Parameter type: `Object`. 
    - `Object:key` Logika jika ditemukan string seperti konfigurasi. 
        - Jika tidak diawali dengan `!`: logika jika ditemukan
        - Jika diawali dengan `!`, maka logika berarti tidak ditemukan
    - `Object:value` pengali jika sesuai dengan logika.
    - Contoh:
    ```JSON
    {
        "fold": {
            " gram": 1,
            " kilogram": 1000,
        }
    }
    ```
    Atau:
    ```JSON
    {
        "fold": {
            " gram": 1,
            "! gram": 1000,
        }
    }
    ```


##### Parameter Type: `Array:output_filter`

| Param                                 | Param Type     | Note |
|---------------------------------------|-------------------|------|
|`start_with`                           | `String`            | Tambahan text di awal 
|`end_with`                             | `String`            | Tambahan text di akhir
|`remove_tags`                          | `Boolean`           | Hapus HTML Tag
|`clear_text`                           | `Array`             | Text yang di hapus. Contoh `["Deskripsi :"]`
|`replace`                              | `Array`             | `Array` berisi `Object`. `Object:key` Yang akan di replace. `Object:value` Kata yang digunakan untuk me*replace*. Contoh: `[{"Foo": "Bar"}]`



##### Parameter Note

- `name` : Nama QSP
- `base_url` : List URL yang support dengan plugin ini. Contoh `["https://www.bukalapak.com", "https://bukalapak.com"]`
- `update_date` : Tanggal Update QSP Format `YYYY-MM-DD`
- `author` : Nama Author Developer QSP
- `author_url` : Link Author Developer QSP
- `selector` : CSS Selector
- `pagination_url_param` : Struktur paginasi pada website. 
    - `"page=[page]"` untuk paginasi URL Query
    - `"page/[page]"` untuk paginasi URL Segment
- `temp_type_data` : Type data sementara sebelum diproses oleh `output_filter` & `output_condition` biasanya digunakan untuk `weight`
- `__alternate` : Array berisikan `Object`, Struktur `Object` seperti pada `patterns\detail`. Alternate akan dibaca jika konfigurasi primer tidak mendapatkan value


### Testing

Untuk melakukan testing, jalankan QloBOT dan buka `localhost:9912/#/tools/qsp_tester` Perhatikan pada tab "Process Log" untuk melihat log pada saat QloBOT memproses QSP untuk membaca website. 

- "List" untuk testing `patterns\list`
- "Detail" untuk testing `patterns\detail`


### Contoh
QSP untuk Bukalapak: [example.qsp](example.qsp)