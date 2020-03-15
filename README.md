# yocto

1. Tải file source code:
- 💻 *$* `mkdir yocto`
  - 📌 Tạo thư mục để chứa source code
- 💻 *$* `cd yocto`
- 💻 *yocto$* `git clone https://github.com/thanhduongvs/meta-yocto-tutorial`
  - 📌 meta-yocto-tutorial là 1 layer mẫu do mình tự tạo
- 💻 *yocto$* `git clone https://git.yoctoproject.org/git/poky`
  - 📌 Đây là source code của Yocto Project
- 💻 *$* `cd poky`
- 💻 *yocto/poky$* `git checkout yocto-2.6.4`
  - 📌 Ở ví dụ này mình dùng branch yocto-2.6.4
  - ⚠️ Câu lệnh sẽ khác nếu dùng yocto project nhỏ hơn 2.4

2. Build yocto:
- 💻 *yocto/poky$* `source oe-init-build-env`
  - 📌 thiết lập các biến môi trường
- 📝 Mở file **poky/build/conf/bblayers.conf** rồi thêm đường dẫn *meta-yocto-tutorial* vào yocto, 
  - 📌 Ví dụ: /home/vanson/yocto/meta-yocto-tutorial

    ```
    # POKY_BBLAYERS_CONF_VERSION is increased each time build/conf/bblayers.conf
    # changes incompatibly
    POKY_BBLAYERS_CONF_VERSION = "2"

    BBPATH = "${TOPDIR}"
    BBFILES ?= ""

    BBLAYERS ?= " \
    /home/vanson/yocto/poky/meta \
    /home/vanson/yocto/poky/meta-poky \
    /home/vanson/yocto/poky/meta-yocto-bsp \
    /home/vanson/yocto/meta-yocto-tutorial \
    "
    ```
- 💻 *yocto/poky/build$* `bitbake bello-image --runall=fetch`
  - 📌 Bước này yocto sẽ tải về các package phục vụ cho việc buid
  - ℹ️ Đối với yocto nhở hơn 2.4 câu lệnh trên được thay thế bằng `bitbake -c fetchall bello-image`
- 💻 *yocto/poky/build$* `bitbake -k bello-image`
  - 📌 Bước này yocto sẽ build image

3. Chạy máy ảo:
- 💻 *yocto/poky/build$* `runqemu qemux86`
  - ⚠️ Sau đó nhập mật khẩu của máy tính của bạn
  - ⚠️ Để đăng nhập máy ảo gõ `root`

- 💻 *yocto/poky/build$* `cd ../../`
- 💻 *$* `bitbake-layers create-layer meta-live`
- 💻 *$* `bitbake-layers show-layers`
- 💻 *$* `bitbake-layers show-layers`
- 💻 */poky/build$* `bitbake -f example`
