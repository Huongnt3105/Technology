* Virtualiztion-ảo hóa được bắt đầu từ những năm 1960, được hiểu như là một phương pháp phân chia hợp lý các tài nguyên hệ thống, được cung cấp bởi các máy chủ, giữa các ứng dụng khác nhau.
* Ảo hóa đề cập tới hành động tạo ra các phiên bản ảo của:
  * **Nền tảng phần cứng máy tính**
  * **Thiết bị lưu trữ**
  * **Tài nguyên mạng máy tính**  
* Nội dung dưới đây sẽ đề cập chủ yếu tới ảo hóa máy chủ - Server virtualization
# Server Virtualization
## Khái niệm
* Ảo hóa máy chủ tạo ra một phiên bản ảo của máy chủ bằng các phân chia phần cứng máy chủ thành 2 hoặc nhiều phân đoạn. Mỗi phân đoạn này hoạt động như một môi trường độc lập của riêng nó 
* Cho phép chạy nhiều hệ điều hành giống hoặc khác nhau, hoàn toàn độc lập, tách biệt với nhau trên cùng một phần cứng máy chủ 
           ![virtualization server](https://github.com/Huongnt3105/Technology/blob/master/images/virtualization_server.png)
## Why virtualizing?
Để thấy rõ sự cần thiết của ảo hóa, ta đi so sánh 2 mô hình trước và sau khi ảo hóa máy chủ
* Trước khi ảo hóa 
   ![Before virtuliaztion server](https://github.com/Huongnt3105/Technology/blob/master/images/1.png)
  * Chỉ 1 hệ điều hành trên mỗi máy
  * Phần cứng và phần mềm được gắn chặt và đi đôi với nhau
  * Khi thực hiện run nhiều ứng dụng trên cùng một máy chủ thường tạo ra xung đột 
  * Không tận dụng triệt để tài nguyên tính toán
* Sau khi ảo hóa 
  ![After virtualization](https://github.com/Huongnt3105/Technology/blob/master/images/2.png)
  * Các máy ảo VM phá vỡ sự phụ thuộc 1:1 giữa OS và phần cứng
  * Quản lý OS+application như là một đơn vị duy nhất bằng cách đóng gói chúng thành VM
  * Không phụ thuộc vào phần cứng
  * Các VM có sự phân tách, độc lập với nhau 
## Server virtualization concepts
Một số concept được sử dụng trong ảo hóa máy chủ
     ![Virtualization concepts](https://github.com/Huongnt3105/Technology/blob/master/images/3.png)
* **Hypervisor**: 
  * Hypervisor như là một lớp phần mềm đặt giữa phần cứng và VM 
  * Cung cấp các truy nhập ảo và điều khiển chúng tới từng VM 
* **VM**: 
  * Máy ảo-VM là một môi trường phần mềm chạy một hệ điều hành và hoạt động như là một máy tính vật lý 
  *  VM được mô tả bởi các file, bao gồm cả trạng thái và cấu hình của chúng
* Lợi ích khi VM được đóng gói bởi các file, cung cấp các khả năng điều khiển VM:
  * Suspend, resume VM
  * Snapshot: tạo ra các bản chụp lưu lại trạng thái của VM tại một thời điểm nhất định, trong trường hợp có lỗi xảy ra có thể thực hiện rolback về trạng thái không bị lỗi đã snapshot trước đó
  * Clone: cho phép tạo ra một VM giống hệt (bao gồm cả cấu hình của VM tại thời điểm đó) với VM được chọn một cách nhanh chóng
  * Migrate: cho phép di chuyển VM từ server này sang server khác 
  * Record, replay, fault tolerance
## Ưu điểm, nhược điểm của ảo hóa máy chủ
* **Ưu điểm**: 
  * Giảm các chi phí vận hành: điện năng, làm mát ...
  * Provisioning tài nguyên tính toán một cách nhanh chóng
  * Tối ưu việc sử dụng tài nguyên tính toán 
  * Các ứng dụng chạy trên các VM được cô lập với nhau tránh xung đột 
  * Sao lưu dễ dàng, tăng cường khả năng chịu lỗi 
  * Quản lý tập trung 
* **Nhược điểm**: 
  * Giảm hiệu năng so với truyền thống do đi qua lớp ảo hóa: tăng độ trễ và nhiều header 
  *  Quản lý tập trung gây ra Single point of failure
  * Công nghệ ảo hóa yêu cầu các máy chủ cấu hình mạnh
  * Có thể không được support bởi tất cả các phần mềm
  * Xem xét vấn đề license của phần mềm (vd VMWare)
## Phân loại hypervisor
Hypervisor thường được chia thành 2 kiểu:
1. Bare-metal hypervisor: Lớp hypervisor được run trực tiếp trên phần cứng để quản lý các guest OS, truy nhập trực tiếp tới các tài nguyên phần cứng mà không thông qua hệ điều hành của server
* Một số cách gọi khác: Native hypervisor
* VD: VMWare ESXi, Hyper-V, Xen, KVM-Qemu
2. Hosted based: được cài đặt và hoạt động như một phần mềm thông thường đặt trên hệ điều hành của server, việc truy nhập tới tài nguyên phần cứng cần đi qua lớp OS của server 
* VD: Qemu, VMWare workstation...
### So sánh các kiểu hypervisor
* Virtualiztion-ảo hóa được bắt đầu từ những năm 1960, được hiểu như là một phương pháp phân chia hợp lý các tài nguyên hệ thống, được cung cấp bởi các máy chủ, giữa các ứng dụng khác nhau.
* Ảo hóa đề cập tới hành động tạo ra các phiên bản ảo của:
  * **Nền tảng phần cứng máy tính**
  * **Thiết bị lưu trữ**
  * **Tài nguyên mạng máy tính**  
* Nội dung dưới đây sẽ đề cập chủ yếu tới ảo hóa máy chủ - Server virtualization
# Server Virtualization
## Khái niệm
* Ảo hóa máy chủ tạo ra một phiên bản ảo của máy chủ bằng các phân chia phần cứng máy chủ thành 2 hoặc nhiều phân đoạn. Mỗi phân đoạn này hoạt động như một môi trường độc lập của riêng nó 
* Cho phép chạy nhiều hệ điều hành giống hoặc khác nhau, hoàn toàn độc lập, tách biệt với nhau trên cùng một phần cứng máy chủ 
           ![virtualization server](https://github.com/Huongnt3105/Technology/blob/master/images/virtualization_server.png)
## Why virtualizing?
Để thấy rõ sự cần thiết của ảo hóa, ta đi so sánh 2 mô hình trước và sau khi ảo hóa máy chủ
* Trước khi ảo hóa 
   ![Before virtuliaztion server](https://github.com/Huongnt3105/Technology/blob/master/images/1.png)
  * Chỉ 1 hệ điều hành trên mỗi máy
  * Phần cứng và phần mềm được gắn chặt và đi đôi với nhau
  * Khi thực hiện run nhiều ứng dụng trên cùng một máy chủ thường tạo ra xung đột 
  * Không tận dụng triệt để tài nguyên tính toán
* Sau khi ảo hóa 
  ![After virtualization](https://github.com/Huongnt3105/Technology/blob/master/images/2.png)
  * Các máy ảo VM phá vỡ sự phụ thuộc 1:1 giữa OS và phần cứng
  * Quản lý OS+application như là một đơn vị duy nhất bằng cách đóng gói chúng thành VM
  * Không phụ thuộc vào phần cứng
  * Các VM có sự phân tách, độc lập với nhau 
## Server virtualization concepts
Một số concept được sử dụng trong ảo hóa máy chủ
     ![Virtualization concepts](https://github.com/Huongnt3105/Technology/blob/master/images/3.png)
* **Hypervisor**: 
  * Hypervisor như là một lớp phần mềm đặt giữa phần cứng và VM 
  * Cung cấp các truy nhập ảo và điều khiển chúng tới từng VM 
* **VM**: 
  * Máy ảo-VM là một môi trường phần mềm chạy một hệ điều hành và hoạt động như là một máy tính vật lý 
  *  VM được mô tả bởi các file, bao gồm cả trạng thái và cấu hình của chúng
* Lợi ích khi VM được đóng gói bởi các file, cung cấp các khả năng điều khiển VM:
  * Suspend, resume VM
  * Snapshot: tạo ra các bản chụp lưu lại trạng thái của VM tại một thời điểm nhất định, trong trường hợp có lỗi xảy ra có thể thực hiện rolback về trạng thái không bị lỗi đã snapshot trước đó
  * Clone: cho phép tạo ra một VM giống hệt (bao gồm cả cấu hình của VM tại thời điểm đó) với VM được chọn một cách nhanh chóng
  * Migrate: cho phép di chuyển VM từ server này sang server khác 
  * Record, replay, fault tolerance
## Ưu điểm, nhược điểm của ảo hóa máy chủ
* **Ưu điểm**: 
  * Giảm các chi phí vận hành: điện năng, làm mát ...
  * Provisioning tài nguyên tính toán một cách nhanh chóng
  * Tối ưu việc sử dụng tài nguyên tính toán 
  * Các ứng dụng chạy trên các VM được cô lập với nhau tránh xung đột 
  * Sao lưu dễ dàng, tăng cường khả năng chịu lỗi 
  * Quản lý tập trung 
* **Nhược điểm**: 
  * Giảm hiệu năng so với truyền thống do đi qua lớp ảo hóa: tăng độ trễ và nhiều header 
  *  Quản lý tập trung gây ra Single point of failure
  * Công nghệ ảo hóa yêu cầu các máy chủ cấu hình mạnh
  * Có thể không được support bởi tất cả các phần mềm
  * Xem xét vấn đề license của phần mềm (vd VMWare)
## Phân loại hypervisor
Hypervisor thường được chia thành 2 kiểu:
1. Bare-metal hypervisor: Lớp hypervisor được run trực tiếp trên phần cứng để quản lý các guest OS, truy nhập trực tiếp tới các tài nguyên phần cứng mà không thông qua hệ điều hành của server
* Một số cách gọi khác: Native hypervisor
* VD: VMWare ESXi, Hyper-V, Xen, KVM-Qemu
2. Hosted based: được cài đặt và hoạt động như một phần mềm thông thường đặt trên hệ điều hành của server, việc truy nhập tới tài nguyên phần cứng cần đi qua lớp OS của server 
* VD: Qemu, VMWare workstation...
## So sánh 
| So sánh                   | Bare-metal hypervisor                                 | Hosted hypervisor                                                                                           
|---------------------------|-------------------------------------------------------|--------------------------------------------------------------------|
| Virtualization type     | Hardware virtualization                               | Software virtualization                  
| Hypervisor Purpose      | Được sử dụng trên các server có mục đích duy nhất    | Sử dụng trên server cung cấp một loạt các phần mềm ứng dụng khác<br>Không thể sử dụng 100% tài nguyên phần cứng cho các VM| 
| Ưu điểm                 | - Hiệu năng tốt hơn, khả năng mở rộng và ổn định<br>- Không phụ thuộc vào OS của server<br>- Khi 1 VM/guest OS có vấn đề không gây ảnh hưởng đến các VM khác trên cùng server| Tương thích tốt hơn với phần cứng server|- Không phụ thuộc vào OS của server|                                      
| Nhược điểm              | Các phần cứng hỗ trợ bị giới hạn| - Tăng overhead gây ảnh hưởng đến hiệu năng<br>- Các hoạt động của hypervisor hoàn toàn phụ thuộc vào OS server<br>- Khi base OS có vấn đề sẽ gây ảnh hướng toàn hệ thống| 
