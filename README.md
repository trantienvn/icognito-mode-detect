# Mục lục

1. [Giới thiệu về trình duyệt ẩn danh](#giới-thiệu-về-trình-duyệt-ẩn-danh)
2. [Trình duyệt ẩn danh (Incognito mode) là gì?](#trình-duyệt-ẩn-danh-incognito-mode-là-gì)
3. [Cách phát hiện người dùng đang sử dụng Incognito mode trên Google Chrome](#cách-phát-hiện-người-dùng-đang-sử-dụng-incognito-mode-trên-google-chrome)
4. [Cách sử dụng](#cách-sử-dụng)
5. [Kết luận](#kết-luận)
#  Giới Thiệu về trình duyệt ẩn danh.
Trong một số trang web các nhà phát triển đều muốn biết người dùng đang hoạt động ở chế độ nào nhiều nhất. Ở đây bạn hiểu ý tôi là gì mà? Như những trang xxx, thì đa số người dùng trong đó có một số ai đang đọc bài này luôn luôn sử dụng trình duyệt ẩn danh hay còn gọi là Incognito mode.

# Trình duyệt ẩn danh (Incognito mode) là gì?
Chrome cũng giống như các trình duyệt khác đều lưu cookie, lịch sử truy cập, các thống kê, nhưng một khi user sử dụng trình duyệt ẩn danh thì khi user đóng của sổ này thì tất cả các thông tin bao gồm cookie, lịch sử truy cập, các thống kê, và các mật khẩu sẽ bị xoá. Điều đó có nghĩa là thông tin duyệt web của bạn tôi không thể được theo dõi trên hệ thống cục bộ

# Cách phát hiện người dùng đang sử dụng Incognito mode trên Google Chrome?
See Demo : Demo
Rất đơn giản API FileSystem một API của javascript sẽ không được cung cấp trên trình duyệt ẩn danh, cho nên các devjs sẽ chỉ cần sử dụng chúng để check và là trả về true or false.

Cú pháp: 
```
function isIncognito(callback){
	
        var fs = window.RequestFileSystem || window.webkitRequestFileSystem;
        if (!fs) {
	
               callback(false);
	
        } else {
              fs(window.TEMPORARY,
	
                100,
	
                callback.bind(undefined, false),
	
               callback.bind(undefined, true)
	
            );
       }
}
```
[See Demo](https://trantienvn.github.io/icognito-mode-detect)

# Cách sử dụng
```
isIncognito(function(itIs){
     if(itIs){
           console.log("You are in incognito mode");
     }else{
           console.log("You are NOT in incognito mode");
	
     }
	
})
```
# 5 - Kết Luận.
Dù bạn thuộc nhà phát triển nào cũng nên cố gắng track được tất cả người ny  dùng từ đó thu thập thói quen của User nhằm đưa ra định hướng stick đúng cho việc phát triển một dự án.

Cảm ơn các ban đã đọc. Happy coding !
