# 🖌️ dash_painter

`dash_painter` là một plugin Flutter giúp bạn vẽ **đường nét đứt (dash lines)** và **đường chấm - gạch (dot-dash)** một cách đơn giản trên `Canvas`.  
Thích hợp dùng trong `CustomPainter`, `Decoration`, hoặc bất kỳ nơi nào sử dụng đối tượng `Canvas`.

---

## 🚀 Cài đặt

Thêm vào file `pubspec.yaml`:

```yaml
dependencies:
  dash_painter: ^1.0.0

# hoặc
flutter pub add dash_painter
```

Sau đó, chạy lệnh sau để cài đặt package:

```bash
flutter pub get
```

## 🎨 Cách sử dụng

1. Dùng trong CustomPainter

```dart
class MyDashedLinePainter extends CustomPainter {
  @override
  void paint(Canvas canvas, Size size) {
    final paint = Paint()
      ..color = Colors.blue
      ..strokeWidth = 2
      ..style = PaintingStyle.stroke;

    final path = Path()
      ..moveTo(0, 0)
      ..lineTo(size.width, 0);

    const DashPainter(span: 4, step: 8).paint(canvas, path, paint);
  }

  @override
  bool shouldRepaint(CustomPainter oldDelegate) => false;
}
```

2. Dùng trong Decoration

```dart
Container(
  width: 200,
  height: 200,
  decoration: BoxDecoration(
    border: Border.all(
      color: Colors.blue,
      width: 2,
    ),
    borderRadius: BorderRadius.circular(20),
    decoration: const DashDecoration(
      span: 4,
      step: 8,
    ),
  ),
)
```

✨ Tính năng

✅ Vẽ đường nét đứt (dashed line)

✅ Vẽ đường chấm - gạch (dot-dash)

✅ Vẽ đường nét đứt trên hình học bất kỳ (path)

✅ Vẽ đường nét đứt trên hình học phức tạp (complex path)

✅ Tùy chỉnh độ dài nét (step), khoảng trắng (span)

✅ Hỗ trợ gradient với DashDecoration

✅ Dễ dùng, không cần widget mới

🧩 API DashPainter
| Thuộc tính | Mô tả | Kiểu | Mặc định |
| ------------ | ----------------------------------------- | -------- | -------- |
| `span` | Độ dài khoảng trắng giữa các nét | `double` | 4.0 |
| `step` | Độ dài nét vẽ (mỗi đoạn) | `double` | 9.0 |
| `pointCount` | Số chấm trong mỗi đoạn | `int` | 0 |
| `pointWidth` | Độ dài mỗi chấm nếu dùng `pointCount > 0` | `double` | 2.0 |

🧱 API DashDecoration
Tất cả thuộc tính của DashPainter +:
| Thuộc tính | Mô tả | Kiểu |
| ---------- | --------------------------------------- | ----------- |
| `radius` | Bo góc hình chữ nhật | `Radius?` |
| `gradient` | Gradient màu viền (SweepGradient, v.v.) | `Gradient?` |

📂 Thư mục mẫu

```dart
dash_painter/
├── lib/
│   └── dash_painter.dart
├── example/
│   └── main.dart
├── README.md
├── LICENSE
└── pubspec.yaml
```

## 📝 Giấy phép

`dash_painter` được cấp phép theo giấy phép MIT.
