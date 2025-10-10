# Unity-JSON-Persistence

[中文](#中文) | [English](#english) 

---
## 中文

### 概述
这是一个用于 **Unity 数据持久化** 的轻量级工具，采用 **JSON 文件** 的方式进行存储与读取。  
支持 **LitJSON** 和 **JsonUtility** 两种序列化器，可根据需求自由切换。

### 功能特点
- 基于文件的 JSON 存储与读取  
- 可选择序列化器：**LitJSON** 或 **JsonUtility**  
- 简洁的静态 API，快速集成  
- 兼容自定义可序列化类

### 安装方法
1. 克隆或下载本仓库。  
2. 将 `JsonMgr.unitypackage` 拖到到 Unity 的 `Assets/` 目录下。  

### 快速开始
```csharp
using UnityEngine;

public class Example : MonoBehaviour
{
    void Start()
    {
        // 创建示例数据
        PlayerProfile profile = new PlayerProfile
        {
            name = "chenhoutao",
            age = 25,
            level = 5
        };

        // 保存为 JSON 文件
        JsonMgr.Instance.SaveData(profile, "player_profile");
        // 从 JSON 文件读取
        PlayerProfile player1 = JsonMgr.Instance.LoadData<PlayerProfile>("player_profile");
    }
}

[System.Serializable]
public class PlayerProfile
{
    public string name;
    public int age;
    public int level;
}
```

### 选择序列化器
- 默认使用 **LitJSON**  
- 切换到 **JsonUtility**：
```csharp
JsonMgr.Instance.SaveData(profile, "player_profile", JsonType.JsonUtility);
```

### 文件存储路径
- 文件默认存储在 `Application.persistentDataPath`
- **Windows**：`C:/Users/<用户名>/AppData/LocalLow/<公司名>/<项目名>`

---

## English

### Overview
Unity data persistence through JSON files with support for LitJSON or JsonUtility.

### Features
- File-based JSON save and load for Unity data persistence  
- Selectable serializers: **LitJSON** or **JsonUtility**  
- Simple static API for quick integration  
- Works with custom serializable classes  

### Installation
1. Clone or download this repository.  
2. Copy the `JsonMgr.unitypackage` into your Unity `Assets/` directory.  

### Quick Start
```csharp
using UnityEngine;

public class Example : MonoBehaviour
{
    void Start()
    {
        PlayerProfile profile = new PlayerProfile
        {
            name = "chenhoutao",
            age = 25,
            level = 5
        };

        // Save to JSON file
        JsonMgr.Instance.SaveData(profile, "player_profile");

        // Load from JSON file
        PlayerProfile player1 = JsonMgr.Instance.LoadData<PlayerProfile>("player_profile");
    }
}

[System.Serializable]
public class PlayerProfile
{
    public string name;
    public int age;
    public int level;
}
```

### Choosing Serializer
- Default: **LitJSON**  
- Switch to JsonUtility:
```csharp
JsonMgr.Instance.SaveData(profile, "player_profile", JsonType.JsonUtility);
```

### File Location
- Files are stored under `Application.persistentDataPath`.  
- Windows: `C:/Users/<UserName>/AppData/LocalLow/<CompanyName>/<ProjectName>`  
- Android/iOS: stored in Unity’s persistent data folder.

### License
- This project is licensed under the MIT License

- **Android/iOS**：存储在 Unity 管理的持久化数据文件夹中

### 许可证
- 本项目采用 MIT 许可协议
