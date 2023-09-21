- [如何调试BuildSystem](#如何调试buildsystem)

如何调试BuildSystem
===
1. 修改BuildProgramForBee.bee.cs文件，将

```csharp
protected BuildProgramForBee(CSharpCompiler compiler)
{
    CSharpConfig = new CSharpProgramConfiguration(CSharpCodeGen.Release, compiler, HostPlatform.IsWindows ? (DebugFormat)DebugFormat.Pdb : DebugFormat.PortablePdb);
}
```
中的`CSharpCodeGen.Release`改成`CSharpCodeGen.Debug`来让创建的`BuildSystem.gen.sln`中添加的子项目以Debug形式

2. 执行`jam BuildSystemProjectFiles`生成Unity.BuildSystem.gen.sln
3. 使用visual studio打开sln，为`Unity.BuildSystem.gen`中的`Debug>Command line arguments`配置编译选项（编译目标），例如`WinPlayerIL2CPP -sCONFIG=release`，将下面的`Working Directory`配置到引擎根目录。
4. 设置Startup项目为Unity.BuildSystem.gen即可启动调试
