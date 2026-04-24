swimlane
    caption Sơ đồ hoạt động: Yêu cầu trả phòng & Hoàn cọc
    
    lane Khách hàng
        start( )
        :Yêu cầu trả phòng & cung cấp hồ sơ;
        |Quản lý / Sale|
        :Tiếp nhận yêu cầu;
        :Kiểm tra hiện trạng phòng & đối chiếu hợp đồng;
        :Tổng hợp & chuyển thông tin cho Kế toán;
        |Kế toán|
        :Xác định tỷ lệ hoàn cọc & các khoản khấu trừ;
        :Lập bảng đối soát / phiếu thanh toán;
        |Quản lý / Sale|
        :Thông báo chi tiết đối soát cho khách;
        |Khách hàng|
        if (Khách đồng ý?) then (Có)
            :Thỏa thuận phương thức hoàn tiền;
            |Kế toán|
            if (Số dư đối soát?) then (Khách phải đóng thêm)
                |Khách hàng|
                :Thanh toán tiền phát sinh;
                |Kế toán|
                :Thu tiền phát sinh;
            else (Được hoàn / Bằng 0)
            endif
            |Quản lý / Sale|
            :Ký biên bản trả phòng & thanh lý hợp đồng;
            |Kế toán|
            :Thực hiện lệnh hoàn tiền (nếu có);
            |Quản lý / Sale|
            :Thu hồi chìa khóa & thẻ từ;
            :Xác nhận khách kết thúc lưu trú;
            |Hệ thống|
            :Cập nhật trạng thái phòng trống;
            stop
        else (Không)
            |Quản lý / Sale|
            :Rà soát lại thông tin (điện, nước, hư hỏng);
            |Kế toán|
            :Cập nhật bảng đối soát;
            detach
        endif
