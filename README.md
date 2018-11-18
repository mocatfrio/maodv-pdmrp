# Power and Delay-aware Multi-path Routing Protocol for Ad Hoc Networks
Implementasi paper berjudul **"Power and Delay-aware Multi-path Routing Protocol for Ad Hoc Networks"** yang dapat diunduh di https://ieeexplore.ieee.org/document/6878956

Oleh: **Hafara Firdausi** (05111540000043)

## Table of Content
- [Power and Delay-aware Multi-path Routing Protocol for Ad Hoc Networks](#power-and-delay-aware-multi-path-routing-protocol-for-ad-hoc-networks)
  - [Table of Content](#table-of-content)
  - [1. Deskripsi Host](#1-deskripsi-host)
  - [2. Dasar Teori](#2-dasar-teori)
    - [2.1 AODV Routing Protocol](#21-aodv-routing-protocol)
    - [2.2 SPR Routing Protocol](#22-spr-routing-protocol)
    - [2.3 AOMDV Routing Protocol](#23-aomdv-routing-protocol)
  - [3. Konsep Modifikasi](#3-konsep-modifikasi)
    - [3.1 PDMRP Routing Protocol](#31-pdmrp-routing-protocol)
  - [4. Implementasi](#4-implementasi)
    - [4.1](#41)
  - [Referensi](#referensi)

## 1. Deskripsi Host
* Sistem Operasi : Linux Mint 18.3 Sylvia
* Aplikasi yang digunakan :
  * NS-2.35 ([Instalasi](/install-ns2.md))

## 2. Dasar Teori
### 2.1 AODV Routing Protocol
* **AODV** (Ad Hoc On-Demand Distance Vector Routing Protocol) adalah salah satu routing protocol reaktif.
* Terdapat 3 jenis paket yang digunakan untuk **route discovery** dan **route maintenance**, yakni:
  * Route Request (RREQ)
  
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
  
    ![Paket RREP](/img/rrep.jpg)

  * Route Error (RERR) 

    ![Paket RERR](/img/rerr.jpg)
  
### 2.2 SPR Routing Protocol
* **SPR** (Stable Path Routing Protocol based on Power Awareness) adalah sebuah on-demand routing protocol yang diusulkan pada paper berikut  https://pdfs.semanticscholar.org/3159/ac48ea17987c3541e636ee431b9450e968aa.pdf 
* Cara kerja:


### 2.3 AOMDV Routing Protocol

## 3. Konsep Modifikasi
### 3.1 PDMRP Routing Protocol
* **PDMRP** (Power and Delay-aware Multi-path Routing Protocol) adalah routing protocol multi-path dengan waktu hidup (lifetime) paling lama di jaringan tanpa penurunan performa dalam hal waktu delay.
*  
* 

  1.  
## 4. Implementasi
### 4.1 

## Referensi
* https://drive.google.com/file/d/0B6aQ8IUEyp5NekhLZWVwV0lRNU0/edit
* https://www.ietf.org/rfc/rfc3561.txt




