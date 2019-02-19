## UTS

**I.**

1.	Unikernel adalah sebuah image yang dapat dieksekusi yang dapat dieksekusi secara native pada hypervisor, tanpa perlu sistem operasi yang terpisah. Image tersebut berisi kode aplikasi, serta semua fungsi sistem operasi yang diperlukan oleh aplikasi itu.
2.	Dockerfile adalah dokumen teks yang berisi semua perintah yang dapat dipanggil pengguna pada baris perintah untuk membuat sebuah image. Menggunakan docker build pengguna dapat membuat build otomatis yang  dapat mengeksekusi beberapa instruksi baris perintah secara berurutan.
3.	Docker Hub adalah repositori berbasis cloud tempat dimana users Docker membuat, menguji, menyimpan, dan mendistribusikan image pada kontainer. Melalui Docker Hub, pengguna dapat mengakses repositori gambar sumber terbuka, dan juga menggunakan ruang untuk membuat repositori pribadi mereka sendiri, fungsi pembuatan otomatis, webhooks dan kelompok kerja.
4.	dockerd adalah proses persisten yang mengelola kontainer. Docker menggunakan binari yang berbeda untuk daemon dan klien. Untuk menjalankan daemon Anda mengetik dockerd.
5.	Dalam domain Cloud Computing, ada berbagai istilah untuk bagian-bagian tertentu dari cloud. Beberapa istilah ini mencakup variasi yang berbeda dari "XaaS(Everithing as a Services)" - yang berarti "sesuatu" sebagai layanan; X adalah variabel yang dapat diubah untuk mewakili beberapa hal. Istilah ini hanya menggambarkan distribusi berbagai komponen TI dalam model layanan Cloud Computing. Semua opsi berikut adalah layanan hosting yang disediakan melalui Cloud, dan termasuk keamanan Cloud; beberapa fokus pada satu aspek TI, sementara yang lain mencakup semuanya sebagai layanan.


**II.**

Keterkaitan antara  Docker CE ( Community editon) dengan docker compose yaitu Dengan docker compose kita bisa menyimpan konfigurasi dalam file, berarti semua perubahan dependency service, seperti versi database dan service lain dapat dimasukkan dalam VCS (Version Control System). Dengan VCS kita dapat lebih mudah men-debug jika terjadi error pada software.



## UAS

**I**

1.	Kubernetes adalah aplikasi cluster management open source yang disponsori oleh Google. Aplikasi ini berasal dari aplikasi internal yang digunakan Google (namanya Borg) untuk mengelola cluster mereka sendiri
2.	Sama seperti docker swarm, kubectl dapat melakukan manajemen container, akan tetapi kubectl merupakan produk yang akan terus berkembang dan akan lebih banyak digunakan dibandingkan dengan docker swarm. 
3.	Pod adalah objek terkecil, paling dasar yang dapat digunakan di Kubernetes. Pod mewakili satu contoh proses yang berjalan di kluster Anda. Pod berisi satu atau lebih kontainer, seperti kontainer Docker. Ketika Pod menjalankan beberapa kontainer, kontainer dikelola sebagai satu kesatuan dan berbagi sumber daya Pod. Secara umum, menjalankan beberapa wadah dalam satu Pod adalah kasus penggunaan tingkat lanjut.
4.	Docker Compose adalah alat untuk mendefinisikan dan menjalankan aplikasi Docker multi-kontainer. Dengan Compose, Anda menggunakan file Compose untuk mengonfigurasi layanan aplikasi Anda. Kemudian, menggunakan satu perintah, Anda membuat dan memulai semua layanan dari konfigurasi Anda.
5.	Docker Machine adalah alat yang memungkinkan Anda menginstal Docker Engine pada host virtual, dan mengelola host dengan perintah mesin docker. Anda dapat menggunakan Mesin untuk membuat host Docker di Mac lokal Anda atau kotak Windows, di jaringan perusahaan Anda, di pusat data Anda, atau di penyedia cloud seperti Azure, AWS, atau Digital Ocean.


**II**

1.	Basic objects kubernetes meliputi:
    * pod
    * services
    * volume
    * NameSpace

2.	Controller kubernetes meliputi:
    * ReplicaSet
    * Deployment
    * StatefulSet
    * DaemonSet
    * Job

3.	Keterkaitan antara basic objects dan controller. Kubernetes berisi sejumlah abstraksi tingkat lebih tinggi yang disebut Controllers. Kontroler dibangun di atas objek dasar, dan menyediakan fungsionalitas tambahan dan fitur kenyamanan.


**III**
Deploy Pod menggunkan Perintah Kubectl
1.  Create a Deployment based on the YAML file:  
kubectl apply -f https://k8s.io/examples/application/deployment.yaml
2.  Display information about the Deployment:  
      kubectl describe deployment nginx-deployment  
      The output is similar to this:  
      user@computer:~/website$ kubectl describe deployment nginx-deployment  
      Name:     nginx-deployment  
      Namespace:    default  
      CreationTimestamp:  Tue, 30 Aug 2016 18:11:37 -0700  
      Labels:     app=nginx  
      Annotations:    deployment.kubernetes.io/revision=1  
      Selector:   app=nginx  
      Replicas:   2 desired | 2 updated | 2 total | 2 available | 0 unavailable  
      StrategyType:   RollingUpdate  
      MinReadySeconds:  0  
      RollingUpdateStrategy:  1 max unavailable, 1 max surge  
      Pod Template:  
      Labels:       app=nginx  
      Containers:  
       nginx:  
          Image:              nginx:1.7.9  
         Port:               80/TCP  
         Environment:        <none>  
         Mounts:             <none>  
       Volumes:              <none>  
      Conditions:  
      Type          Status  Reason  
       ----          ------  ------
       Available     True    MinimumReplicasAvailable  
       Progressing   True    NewReplicaSetAvailable  
      OldReplicaSets:   <none>  
      NewReplicaSet:    nginx-deployment-1771418926 (2/2 replicas created)  
      No events.  
3.  List the pods created by the deployment:  
      kubectl get pods -l app=nginx  
      The output is similar to this:  
      NAME                                READY     STATUS    RESTARTS   AGE  
      nginx-deployment-1771418926-7o5ns   1/1       Running   0          16h  
      nginx-deployment-1771418926-r18az   1/1       Running   0          16h  
4.  Display information about a pod:  
      kubectl describe pod <pod-name>  
      where <pod-name> is the name of one of your pods.  
