# Phú Quốc — Voxel & Map Data 3D

Bản đồ địa hình Phú Quốc dựng bằng khối voxel, viết thành một file HTML tự chứa để nhúng vào Wix. Dùng three.js r171 WebGPURenderer, tự chuyển sang WebGL2 khi trình duyệt không có WebGPU.

- **Địa hình:** mỗi khối rộng một điểm ảnh của dữ liệu cao độ (≈ 37,6 m). Màu lấy theo độ cao và lớp phủ mặt đất. Ánh sáng và bóng góc khối được tính sẵn.
- **Lớp dữ liệu:** đường, phà, hạ tầng, du lịch, giao thông và các công trình vẽ bằng nét.
- **Điều khiển:** kéo để xoay, lăn chuột để phóng to vào đúng chỗ con trỏ; có nút về khung toàn đảo và nút nghiêng.

## Ghi chú Safari

three r171 đọc texture lọc "Nearest" bằng `textureLoad` ở chỉ số `floor(u·size)`. Khi u = 1, chỉ số này vượt ra ngoài ảnh; Safari trả về màu đen nên hiện vạch đen dọc ranh khối. File kẹp toạ độ vân đá lùi vào nửa texel để tránh lỗi này. three đã sửa từ r183 ([PR #32826](https://github.com/mrdoob/three.js/pull/32826)).
