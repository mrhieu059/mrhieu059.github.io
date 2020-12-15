---
layout: post
title: Gõ tiếng việt trên Linux
categories: GNU Linux
---
# Hướng dẫn gõ tiếng việt trên Linux bằng _Fcitx_
Như mình biết thì cộng đồng Linux ngày càng được nhiều người biết đến, và một vấn đề mà các bạn mới chuyển sang Linux gặp phải đó là Linux không hỗ trợ gõ bộ gõ tích hợp sắn như Windows. Và điều này sẽ thật bất tiện nếu bạn nào hay nhắn tin, soạn thảo văn bản trên Linux và cần sử dụng tiếng việt. Thế nên là mình xin hướng dẫn các bạn cách cài đặt bộ gõ tiếng việt trên Linux.

Để gõ được tiếng việt trên Linux thì theo mình biết là có 2 cách
1. Sử dụng _Ibus_ (Ibus-unikey, Ibus-bamboo)
2. Sử dụng _Fcitx_ (fcitx-unikey)

Dựa trên trải nghiệm của mình thì Fcitx có tốc độ phản hồi tốt hơn Ibus. Thế nên là trong bài này mình sẽ chỉ hướng dẫn gõ tiếng việt với fcitx.

* Yêu cầu:
	* Biết sử dụng command line cơ bản
	* Biết cài ứng dụng từ repo của bản phân phối linux các bạn đang sử dụng.
		* Ubuntu: `apt-get install package_name`
		* Arch: `pacman -S package_name`
		* Void: `xbps-install package_name`
	
Đầu tiên các bạn sẽ cài Fcitx và bộ gõ unikey, ở đây mình dùng Arch linux nên câu lệnh có thể sẽ khác các bạn. Tùy vào bạn dùng cái nào mà chỉnh cho phù hợp.

1. `pacman -S fcitx-im fcitx-unikey fcitx-configtool`
2. Sau khi hoàn tất thì các bạn bắt đầu đặt biến môi trường (environment) trong **$HOME/.pam_environment**
	>GTK_IM_MODULE DEFAULT=fcitx
	>	
	>QT_IM_MODULE  DEFAULT=fcitx
	>	
	>XMODIFIERS    DEFAULT=\@im=fcitx

3. Tiếp đến các bạn sẽ muốn Fcitx bắt đầu tự động khi các bạn khởi động máy tính. Ở đây tùy vào môi trường bạn sử dụng là gì thì cách cài đặt sẽ khác nhau. Mình chỉ sử dụng windows manager và startx nên mình chỉ cần thêm dòng sau vào **$HOME/.xinitrc**
	> fcitx &
	>
	> WM_các_bạn_sử_dụng



4. Bây giờ các bạn khởi động lại máy tính để các biến môi trường có hiệu lực.
5. Tiếp đến các bạn mở giao diện cấu hình bằng cách mở chương trình `fcitx-configtool`. 
6. Ở góc dưới bên trái các bạn sẽ thấy dấu +, đó là nơi các bạn thêm bộ gõ tiếng việt. 

7. Bấm vào dấu cộng
8. Một hộp thoại để chọn bộ gõ sẽ hiện lên
9. Các bạn bỏ chọn `Only Show Curent Language`
10. Kéo xuống gần dưới các bạn sẽ thấy Unikey
11. Chọn Unikey sau đó chọn OK.
![Input method](/res/input-method.png)
11. Bây giờ các bạn mở thử một ứng dụng và nhấn tổ hợp phím `CTRL+SPACE` các bạn sẽ thấy hộp thoại Unikey hiện lên.
12. Tức là bộ gõ Unikey đang được kích hoạt và các bạn có thể gõ tiếng việt được rồi.
13. Để chuyển bộ gõ sang lại tiếng anh thì các bạn lại nhấn tổ hợp phím `CTRL+SPACE`

## Hy vọng các bạn có thể gõ được tiếng việt.

--- 


>Note: Trong trường hợp các bạn gõ tiếng việt trong commandline terminal và nó không nhận chữ thì các bạn nên kiểm tra lại xem là biến LANG đã được đặt đúng chưa. Mình đang ở US nên mình sẽ đặt biến LANG của mình là LANG=en_US.utf8, nếu các bạn đã đặt biến LANG thì nó sẽ nhìn giống như này.

![Locale](/res/locale-info.png)
