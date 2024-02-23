# 项目名称：Surprising ATCP

## 项目介绍

Surprising ATCP 是一款基于 Java 的高性能 Web 服务器，它为用户提供了强大的网络服务功能。该项目融合了防火墙、流量限制、请求转发等多种功能，旨在满足企业级应用的需求。Surprising ATCP 的设计注重多线程支持、高并发处理，同时融入了一些令人惊喜的特色元素，如香蕉标志，以提供用户更加愉快的开发体验。

## 使用说明

### 导入包

1. 将项目的 jar 包添加到您的项目中。

2. 导入 `com.surprisingatcp` 包：

```java
import com.surprisingatcp.*;
```

### 创建服务器实例

```java
ATCPServer server = new ATCPServer();
```

### 配置服务器

```java
// 设置服务器端口
server.setPort(8080);

// 启用防火墙
server.enableFirewall();
server.addFirewallRule(FirewallRule.ALLOW, "127.0.0.1");
server.addFirewallRule(FirewallRule.ALLOW, "192.168.1.0/24");
server.addFirewallRule(FirewallRule.BLOCK, "10.0.0.1");

// 启用流量限制
server.enableThrottling(1000); // 设置每秒最大请求数为1000

// 启用请求转发
server.enableForwarding();
server.addForwardingRule("/api/*", "http://backend-server:8081/api/");
server.addForwardingRule("/static/*", "/var/www/static/");
```

### 启动服务器

```java
server.start();
```

### 示例

#### 1. 基本用法

```java
public class Main {
    public static void main(String[] args) {
        ATCPServer server = new ATCPServer();
        server.setPort(8080);
        server.start();
        System.out.println("Server started on port 8080");
    }
}
```

#### 2. 配置防火墙

```java
server.enableFirewall();
server.addFirewallRule(FirewallRule.ALLOW, "127.0.0.1");
server.addFirewallRule(FirewallRule.ALLOW, "192.168.1.0/24");
server.addFirewallRule(FirewallRule.BLOCK, "10.0.0.1");
```

#### 3. 配置流量限制

```java
server.enableThrottling(1000); // 设置每秒最大请求数为1000
```

#### 4. 配置请求转发

```java
server.enableForwarding();
server.addForwardingRule("/api/*", "http://backend-server:8081/api/");
server.addForwardingRule("/static/*", "/var/www/static/");
```

## 注意事项

- 请确保您的项目具有足够的权限来监听指定的端口和访问所需的资源。

- 请根据实际需求调整防火墙、流量限制和请求转发的配置。

## 版权信息

本项目基于 [MIT License](LICENSE) 进行分发和使用。
