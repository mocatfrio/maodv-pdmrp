# Power and Delay-aware Multi-path Routing Protocol

Oleh : **Hafara Firdausi** (05111540000043)

## Table of Content
- [Power and Delay-aware Multi-path Routing Protocol](#power-and-delay-aware-multi-path-routing-protocol)
  - [Table of Content](#table-of-content)
  - [1. Pendahuluan](#1-pendahuluan)
  - [1.1 Deskripsi Sistem](#11-deskripsi-sistem)
  - [1.2 Deskripsi Paper](#12-deskripsi-paper)
  - [2. Dasar Teori](#2-dasar-teori)
    - [2.1 AODV Routing Protocol](#21-aodv-routing-protocol)
    - [2.2 SPR Routing Protocol](#22-spr-routing-protocol)
  - [3. Konsep Modifikasi](#3-konsep-modifikasi)
    - [3.1 PDMRP Routing Protocol](#31-pdmrp-routing-protocol)
  - [4. Implementasi](#4-implementasi)
    - [4.1](#41)
    - [4.2](#42)
  - [Referensi](#referensi)

## 1. Pendahuluan 
## 1.1 Deskripsi Sistem
* Sistem Operasi : Linux Mint 18.3 Sylvia
* Aplikasi yang digunakan :
  * NS-2.35 ([Instalasi](/install-ns2.md))
  * Netbeans for C/C++ Development ([Instalasi](https://websiteforstudents.com/how-to-install-netbeans-on-ubuntu-16-04-17-10-18-04/))

## 1.2 Deskripsi Paper
* Judul Paper : **Power and Delay-aware Multi-path Routing Protocol for Ad Hoc Networks**
* Sumber : https://ieeexplore.ieee.org/document/6878956

## 2. Dasar Teori
### 2.1 AODV Routing Protocol
* **AODV** (Ad Hoc On-Demand Distance Vector Routing Protocol) adalah salah satu routing protocol reaktif.
* Terdapat 3 jenis paket yang digunakan untuk **route discovery** dan **route maintenance**, yakni:
  * Route Request (RREQ)
    Memiliki format paket sebagai berikut:
  
    ![Paket RREQ](/img/rreq.jpg)

    Keterangan:
      * **Type** : Tipe paket (RREQ = 1)
      * **|J|R|G|D|U|** : Flag yang menunjukkan keadaan paket
      * **Reserved** : Default 0, diabaikan
      * **Hop Count** : Jumlah hops dari node asal ke node yang sedang meng-handle RREQ saat ini
      * **RREQ ID** : Nomor urut unik yang mengidentifikasi RREQ tertentu 
      * **Destination IP Address** : Alamat IP tujuan
      * **Destination Sequence Number** : Nomor urutan terakhir yang diterima oleh node asal untuk menuju ke node tujuan
      * **Originator IP Address** : Alamat IP asal (yan memulai RREQ)
      * **Originator Sequence Number** : Nomor urutan saat ini 

  * Route Reply (RREP)
    Memiliki format paket sebagai berikut:

    ![Paket RREP](/img/rrep.jpg)

  * Route Error (RERR) 
    Memiliki format paket sebagai berikut:

    ![Paket RERR](/img/rerr.jpg)
  
### 2.2 SPR Routing Protocol
* **SPR** (Stable Path Routing Protocol based on Power Awareness) adalah sebuah on-demand routing protocol yang diusulkan pada paper berikut  https://pdfs.semanticscholar.org/3159/ac48ea17987c3541e636ee431b9450e968aa.pdf 
* SPR mencari rute paling optimal dari node asal ke node tujuan pada jaringan MANET. Rute ini stabil dipandang dari segi sisa waktu hidup baterai.


## 3. Konsep Modifikasi
Routing protocol yang diusulkan dalam paper ini diberi nama PDMRP yakni Power and Delay-aware Multi-path Routing Protocol.

### 3.1 PDMRP Routing Protocol
* **PDMRP** (Power and Delay-aware Multi-path Routing Protocol) adalah routing protocol yang memiliki tujuan memilih multi-path (path lebih dari satu) dengan lifetime terpanjang, tanpa mengalami penurunan performa dipandang dari segi waktu delay. 
* Untuk mencapai tujuan tersebut, maka perlu dihitung Cost (C) untuk setiap rute dengan rumus berikut:
  ```
  C = ML / NH
  ```
  Keterangan:
  * **ML** (Sisa hidup minimum)
  * **NH** (Jumlah hop dalam suatu path)
* Sehingga, cara kerja AODV dimodifikasi menjadi sebagai berikut:
  1. Ketika **node intermediate** menerima paket RREQ lebih dari satu dari sumber yang sama, maka ia akan menghitung C pada setiap RREQ, kemudian me re-broadcast paket dengan nilai C paling besar (paket lain di-drop).
  2. Setelah menerima paket RREQ pertama, **node tujuan** akan menunggu paket RREQ lain dari path yang berbeda dengan waktu yang telah ditentukan. Kemudian, node tujuan akan akan mengirim paket RREP ke node asal.
  3. **Node asal** akan menerima paket RREP dari semua path dan memilih rute primer dengan nilai C paling besar. Rute selanjutnya dijadikan rute sekunder, tersier, dst. Hal ini dilakukan untuk berjaga-jaga jika terjadi kegagalan atau kerusakan rute primer, maka pengiriman data akan diarahkan ke rute sekunder tanpa harus melakukan route discovery kembali.

## 4. Implementasi
Dari dasar teori dan konsep modifikasi diatas, maka saya memodifikasi codingan AOMDV di bagian:
### 4.1
### 4.2

## Referensi
* [A Tutorial on the Implementation of Ad-hoc On Demand Distance Vector (AODV) Protocol in Network Simulator (NS-2)](https://drive.google.com/file/d/0B6aQ8IUEyp5NekhLZWVwV0lRNU0/edit)
* [Ad hoc On-Demand Distance Vector (AODV) Routing](https://www.ietf.org/rfc/rfc3561.txt)




