---
layout: post
title: KeePass - Trình quản lý mật khẩu an toàn
date: 2020-12-19 12:23:20
summary: 1Password, Last Pass, Sticky Password, DashLane,... là những trình quản lý mật khẩu khá phổ biến bởi vì tính tiện lợi và an toàn của nó. Tuy nhiên, nhiều bạn sẽ cho rằng mật khẩu được lưu bên thứ ba sẽ không đảm bảo an toàn, nên vẫn còn ngập ngừng chưa muốn sử dụng.
categories: Goodreads

---

1Password, Last Pass, Sticky Password, DashLane,... là những trình quản lý mật khẩu khá phổ biến bởi vì tính tiện lợi và an toàn của nó. Tuy nhiên, nhiều bạn sẽ cho rằng mật khẩu được lưu bên thứ ba sẽ không đảm bảo an toàn, nên vẫn còn ngập ngừng chưa muốn sử dụng.

Trình quản lý mật khẩu là nơi để bạn lưu trữ mật khẩu an toàn và phải đảm bảo chỉ có bạn có thể mở được mật khẩu để xem. Nếu vi phạm điều trên bạn sẽ có nguy cơ rò rỉ mật khẩu.

# Lý do nên sử dụng

Hiện tại, phần lớn người dùng Internet sẽ sử dụng chung một mật khẩu cho nhiều dịch vụ khác nhau. Điều đó đồng nghĩa với việc, nếu chẳng may mật khẩu bạn bị rò rỉ thì dường như tất cả các dịch vụ của bạn đều bị rò rỉ và việc đổi mật khẩu khá mất thời gian. Các tiêu chuẩn để đặt được mật khẩu an toàn như tối thiểu một ký tự viết hoa, viết thường, số, ký tự đặc biệt và độ dài khuyến nghị từ 8--15 ký tự và mỗi dịch vụ bạn sẽ sử dụng một mật khẩu khác nhau. Ví dụ, mật khẩu của bạn có thể trông như thế này:

-   gXV4h'vIN~rL
-   u=crN$Q9X"G3

Và mỗi dịch vụ bạn chỉ sử dụng một mật khẩu khác nhau. Với những bạn siêu trí nhớ thì đơn giản, nhưng với đại đa số mọi người sẽ khá vất vả để nhớ 2--3 mật khẩu như vậy chứ chưa tính tới tất cả các dịch vụ. Vì vậy, trình quản lý mật khẩu ra đời để giải quyết vấn đề như vậy, bạn chỉ cần nhớ một mật khẩu duy nhất để mở khoá tất cả các mật khẩu khác.

# Các trình quản lý mật khẩu

Ưu điểm chung của các trình quản lý mật khẩu như 1Password, Last Pass, Sticky Password, Dashlane,... nằm ở tính tiện lợi của nó. Đa số có tính năng tự động điền mật khẩu (auto fill) vào ô đăng nhập nhằm tránh người khác nhìn thấy cử chỉ tay lúc nhập, tránh keylogger cũng như thao tác sẽ nhanh hơn, tiện hơn cho người sử dụng.

Nhược điểm chung của các trình quản lý mật khẩu trên là nhược điểm khá lớn cũng như đây cũng là vấn đề chính làm cho người dùng chưa muốn sử dụng vì độ an toàn bảo mật. Vì được cung cấp bên thứ ba, mật khẩu của bạn sẽ được lưu trữ bên thứ ba mặc dù có mã hoá mật khẩu của bạn rồi, nhưng tui là tui vẫn không tin đấy thì sao nào. Vì đã có những trường hợp một số nhà cung cấp trên đã dính phốt rò rỉ dữ liệu.

Tuy nhiên, vẫn còn một cách để đảm bảo an toàn mật khẩu của bạn, chính là sử dụng KeePass.

# KeePass là gì?

KeePass cũng là trình quản lý mật khẩu nhưng các mật khẩu của bạn sẽ được mã hoá và lưu trong máy của bạn mà không phải lưu bên thứ ba nào khác, bạn được toàn quyền quyết định file chứa mật khẩu của bạn. KeePass cũng là phần mềm mã nguồn mở nên bạn hãy yên tâm rằng KeePass được đông đảo mọi người trên thế giới xem mã nguồn để kiểm tra độ an toàn, sửa lỗi bảo mật thường xuyên.

Vấn đề lớn nhất của KeePass thua các trình quản lý mật khẩu ở trên là do file chứ mật khẩu bạn chỉ được lưu ở máy bạn nên sẽ không có khả năng đồng bộ hoá giữa các máy được, cũng như KeePass không có tính năng auto fill mà thay vào đó là auto type, tức là KeePass sẽ tự động gõ trên ô đăng nhập. Tuy nhiên, mình đã tìm ra cách để khắc phục những nhược điểm trên và tìm thêm một số tính năng hay ho mà các trình quản lý mật khẩu khác không có.

## Hướng dẫn cơ bản

[KeePass](https://keepass.info/download.html)

[OneDrive](https://levandong.com/2020/12/keepass-trinh-quan-ly-mat-khau-an-toan/)

Bạn có thể tải hai phần mềm ở trên để có thể sử dụng, với OneDrive là tuỳ chọn, bạn có thể chọn nhà cung cấp khác để thay thế. Để trực quan hơn cũng như tránh bài viết dài, bạn có thể xem video ở cuối bài để biết các thao tác nhé. Video bao gồm các thao tác:

-   Tạo file chứa mật khẩu mới.
-   Tạo một tài khoản trong KeePass.
-   Tạo mật khẩu random.
-   Cách thiết lập tính năng Auto Type như ý muốn.
-   Cài đặt các Plugin khuyến nghị.
-   Cách đồng bộ hoá mật khẩu.
-   Cách sử dụng auto fill trên nền web.
-   Tinh chỉnh một số cài đặt cần thiết.

## Đồng bộ mật khẩu

Phần này rất đơn giản, bạn có thể sử dụng các nhà cung cấp dịch vụ lưu trữ như OneDrive, Google Drive, Dropbox,... để đồng bộ hoá. Bạn cần phải tải ứng dụng tương ứng với nhà cung cấp về máy tính và cài đặt, ở đây mình sẽ dùng OneDrive vì có sẵn trên máy Windows 10. Ngoài ra còn một lý do sử dụng nữa, bạn thay đổi dữ liệu thì OneDrive sẽ tạo ra các phiên bản, nếu lỡ bạn lỗi thì hoàn toàn có thể khôi phục. KeePass chính chủ tải từ web, OneDrive của Microsoft thì quá an tâm để sử dụng rồi còn gì nữa.

## Sử dụng tính năng Auto fill với Plugin

Sức mạnh của KeePass nằm ở Plugin. Bạn có thể mở rộng các tính năng mà KeePass cung cấp, khá nhiều đấy, mình đã và đang dùng hài lòng đến mức không có lý do gì để sử dụng các trình quản lý khác.

[Github KeePassHttp](https://github.com/pfn/keepasshttp/)

[Download KeePassHttp](https://raw.github.com/pfn/keepasshttp/master/KeePassHttp.plgx)

[KeePass Helper](https://keepass.info/plugins.html#kphelper)

Sau khi bạn tải KeePassHttp về và bỏ vào thư mục Plugin, bạn hãy vào KeePass Helper và chọn extension phù hợp với trình duyệt chính mà bạn sử dụng, ở đây mình sử dụng Firefox. Bạn hãy cấp quyền, đặt tên khi extension yêu cầu là hoàn thành.

## Sử dụng TOTP

Đây là minh chứng cho sức mạnh của KeePass, thay vì bạn cài Auth trên điện thoại rất mất thời gian, nên KeePass có plugin cho phép bạn lưu OTP trên KeePass luôn để an toàn hơn vì file mật khẩu chỉ có bạn mở được thôi nên OTP cũng thế. Ngoài ra bạn lưu trong điện thoại thường các Auth không có tính năng đặt mật khẩu để truy cập hoặc trường hợp bạn làm mất điện thoại thì khá phiền để đăng nhập vào tài khoản. Vì đây là tính năng khá hữu ích và cũng khá nguy hiểm nên mình sẽ không hướng dẫn chi tiết, bạn nào muốn có thể vọc thử hoặc để lại bình luận để nắm được nhu cầu của các bạn.

[KeeTrayTOTP](https://keepass.info/plugins.html#keetraytotp)

## Sử dụng trên điện thoại Android

Khi bạn sử dụng mật khẩu dài, khó đoán và khó nhớ như vậy, việc đăng nhập trên điện thoại cũng khá khó khăn và nhu cầu của bạn không muốn nhập bằng tay và phải đồng bộ mật khẩu với máy tính. Thật may mắn, mình tìm ra ứng dụng open source và có trên cửa hàng Google Play. Một lưu ý, khi bạn sử dụng ứng dụng sẽ yêu cầu cấp quyền ghi và đọc trong OneDrive, để khắc phục điều này bạn có thể share file đó cho một tài khoản clone nào đó, cấp quyền chỉnh sửa file và dùng tài khoản clone đó để đăng nhập và cấp quyền cho ứng dụng.

[Github](https://github.com/PhilippC/keepass2android/)

[Google Play](https://play.google.com/store/apps/details?id=keepass2android.keepass2android)

Video hướng dẫn:
<iframe width="560" height="315" src="https://www.youtube.com/embed/rTcRirpUdNY" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>