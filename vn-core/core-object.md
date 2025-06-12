# Object VNCore

## Giới thiệu

**Object VNCore** là nền tảng của framework `vn-core`, cung cấp các chức năng và tiện ích thiết yếu để quản lý cơ chế gameplay, dữ liệu người chơi và tương tác tài nguyên tổng thể của máy chủ. Trang này sẽ hướng dẫn bạn các tính năng chính, phương thức và thực tiễn tốt nhất để sử dụng Object VNCore một cách hiệu quả.

### Cách truy cập Object VNCore


Chúng tôi khuyến nghị bạn chỉ lọc và lấy những phần cần thiết của core object thay vì import toàn bộ, trừ khi thực sự cần!
Để tương tác với đối tượng VNCore trong script của bạn, hãy sử dụng mẫu sau ở đầu script:

* Luôn lưu đối tượng VNCore vào một biến cục bộ để tránh gọi lại `exports` nhiều lần

```lua
local VNCore = exports['vn-core']:GetCoreObject()
```

Từ phiên bản `vn-core` 1.3.0 (kiểm tra trong fxmanifest.lua), bạn có thể chọn lấy những phần mình cần từ core object thay vì import toàn bộ! Thay đổi này giúp giảm lượng bộ nhớ sử dụng trong mỗi script vì import toàn bộ core sẽ gây tốn tài nguyên không cần thiết.

```lua
-- Chỉ cần truy cập các hàm của core object!
local VNCore = exports['vn-core']:GetCoreObject({'Functions'})

-- Bây giờ bạn có thể sử dụng:
-- VNCore.Functions

-- Cần truy cập cả Functions và Shared!
local VNCore = exports['vn-core']:GetCoreObject({'Functions', 'Shared'})

-- Bây giờ bạn có thể sử dụng:
-- VNCore.Functions
-- VNCore.Shared
```

### Các hàm Exported

* Từ phiên bản `vn-core` 1.3.0, tất cả các hàm trong core object đều được export, vì vậy nếu chỉ cần một hàm, bạn không cần import toàn bộ! Điều này rất tiện lợi nếu bạn là người viết script hỗ trợ nhiều framework khác nhau và không cần tất cả thông tin của core. Bạn chỉ cần gọi hàm mình cần.

```lua
local function getPlayer(source)
    return exports['vn-core']:GetPlayer(source)
end
```

### Các tính năng chính

| `Functions` | Bộ sưu tập các hàm tiện ích cho các thao tác máy chủ và người chơi thông dụng. |
| ----------- | ----------------------------------------------------------------------------- |

| `Players` | Bảng chứa tất cả người chơi đang kết nối. |
| --------- | ----------------------------------------- |

| `Shared` | Dữ liệu dùng chung như vật phẩm, xe, nghề nghiệp. |
| -------- | ----------------------------------------------- |

| `Config` | Bảng cấu hình chính cho `vn-core` |
| -------- | ---------------------------------- |

| `Commands` | Đăng ký các lệnh tuỳ chỉnh cho server và client. |
| ---------- | ------------------------------------------------ |

## Ví dụ sử dụng

### Truy cập dữ liệu người chơi

* Bạn có thể dùng Object VNCore để lấy dữ liệu người chơi

```lua
local VNCore = exports['vn-core']:GetCoreObject()

local function getPlayerJob(source)
    local player = VNCore.Functions.GetPlayer(source)
    if player then
        local job = player.PlayerData.job
        print("Nghề nghiệp của người chơi:", job.name)
    end
end
```

### Sử dụng dữ liệu dùng chung

* Truy cập dữ liệu dùng chung như vật phẩm, xe, nghề nghiệp

```lua
local VNCore = exports['vn-core']:GetCoreObject()

-- Lấy thông tin một vật phẩm cụ thể
local item = VNCore.Shared.Items['water']
print("Tên vật phẩm:", item.name)
print("Nhãn vật phẩm:", item.label)
```

### Đăng ký lệnh

* Object VNCore cho phép bạn đăng ký các lệnh tuỳ chỉnh cho server

```lua
local VNCore = exports['vn-core']:GetCoreObject()

VNCore.Commands.Add('greet', 'Gửi lời chào', {}, false, function(source, args)
    local name = args[1] or 'người chơi'
    TriggerClientEvent('chat:addMessage', source, {
        template = '<div class="chat-message">Xin chào, {0}!</div>',
        args = { name }
    })
end)
```