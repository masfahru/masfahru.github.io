---
title: "Benchmark Web Framework: Go vs Javascript"
date: 2022-09-20
externalUrl: "https://www.linkedin.com/posts/imamfahrurrofi_web-framework-benchmark-nodejs-vs-go-activity-6976213913256300544-aQct"
summary: "Benchmark beberapa web framework Golang, Node, Deno, dan Bun dengan menggunakan container untuk mengetahui kecepatan pemrosesan payload pada HTTP Method POST di setiap framework."
showReadingTime: true
showWordCount: true
showSummary: true
categories: ["Go", "Node"]
tags: ["Benchmark", "Web-framework"]
---
<img class="thumbnailshadow" src="featured.webp"/>
{{< alert >}}
Artikel ini berasal dari publikasi di Linkedin pada tautan <a target="_blank" href="https://www.linkedin.com/posts/imamfahrurrofi_web-framework-benchmark-nodejs-vs-go-activity-6976213913256300544-aQct">berikut ini</a>.
{{</ alert >}}

Karena penasaran dengan performa beberapa web framework dari Nodejs dan Golang, ditambah adanya keinginan untuk belajar pemrograman backend Golang, maka saya buatlah benchmarknya.

Web framework yang dites:

- Nodejs: ExpressJs, Fastify, dan Hyper-Express
- Golang: Echo, Fiber, dan Native (net/http).
- Bunjs: Honojs
- Deno: Honojs

## Metode Benchmark

Terdapat dua metode untuk test, yakni:

- TEST-GET: 10000 request GET dibagi 100 concurrent users, response berupa JSON berisi status: "OK".
- TEST-POST: 10000 request POST dibagi 100 concurrent users, request body berupa JSON dengan ukuran file 52KB, response berupa JSON berisi data yang dikirim pada request body.

Metode penilaian:
Setiap tes dilakukan 3 kali pada masing-masing web framework, diambil data dengan request per detik terbesar.

Tools:

- Docker desktop
- Cassowary http load testing tool
- Laptop keluaran tahun 2015 core i5 - vcpu 4 - ram 16GB

Urutan tes :

1. Node Express
2. Node Fastify
3. Node Hyper-Express
4. Go Echo
5. Go Fiber
6. Go Native (net/http)
7. Deno Honojs
8. Bun Honojs

## Hasil

TEST-GET:

- Node-ExpressJs: 1126 req/s (Rank 8)
- Node-Fastify: 3258 req/s (Rank 7)
- Node-Hyper-Express: 5458 req/s (Rank 5)
- Go-Echo: 5757 req/s (Rank 3)
- Go-Fiber: 6600 req/s (Rank 1)
- Go-Native: 5650 req/s (Rank 4)
- Deno-Hono: 3924 req/s (Rank 6)
- Bun-Hono: 5819 req/s (Rank 2)

TEST-POST:

- Node-ExpressJs: 252 req/s (Rank 8)
- Node-Fastify: 289 req/s (Rank 4)
- Node-Hyper-Express: 346 req/s (Rank 1)
- Go-Echo: 270 req/s (Rank 6)
- Go-Fiber: 314 req/s (Rank 3)
- Go-Native: 265 req/s (Rank 7)
- Deno-Hono: 285 req/s (Rank 5)
- Bun-Hono: 317 req/s (Rank 2)

Berdasarkan hasil di atas, dapat diketahui bahwa rata-rata performa web framework golang lebih baik dan lebih stabil daripada web framework Nodejs. Namun dengan adanya hasil yang cukup baik pada Node Hyper-Express dan Bunjs, hal ini memberi tahu bahwa Javascript masih memiliki kemampuan untuk bersaing dengan Golang.

Jika rekan-rekan ingin mencoba untuk mem-benchmark sendiri, silahkan clone dan jalankan repository berikut: <https://github.com/masfahru/benchmark-web-framework>
