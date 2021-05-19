# 修改默认程序



对于本教程，您将使用具有分配和检索角色功能的程序替换模板源代码文件。

修改默认程序：

1. 在文本编辑器中打开src/access\_hello/main.mo文件，然后删除现有内容。
2. 将以下示例代码复制并粘贴到文件中：

```text
// Import base modules
import AssocList "mo:base/AssocList";
import Error "mo:base/Error";
import List "mo:base/List";
shared({ caller = initializer }) actor class() {
 // Establish role-based greetings to display
 public shared({ caller }) func greet(name : Text) : async Text {
 if (has_permission(caller, #assign_role)) {
 return "Hello, " # name # ". You have a role with administrative privileges."
 } else if (has_permission(caller, #lowest)) {
 return "Welcome, " # name # ". You have an authorized account. Would you like to play a game?";
 } else {
 return "Greetings, " # name # ". Nice to meet you!";
 }
 };
 // Define custom types
 public type Role = {
 #owner;
 #admin;
 #authorized;
 };
 public type Permission = {
 #assign_role;
 #lowest;
 };
 private stable var roles: AssocList.AssocList<Principal, Role> = List.nil();
 private stable var role_requests: AssocList.AssocList<Principal, Role> = List.nil();
 func principal_eq(a: Principal, b: Principal): Bool {
 return a == b;
 };
 func get_role(pal: Principal) : ?Role {
 if (pal == initializer) {
 ?#owner;
 } else {
 AssocList.find<Principal, Role>(roles, pal, principal_eq);
 }
 };
 // Determine if a principal has a role with permissions
 func has_permission(pal: Principal, perm : Permission) : Bool {
 let role = get_role(pal);
 switch (role, perm) {
 case (?#owner or ?#admin, _) true;
 case (?#authorized, #lowest) true;
 case (_, _) false;
 }
 };
 // Reject unauthorized user identities
 func require_permission(pal: Principal, perm: Permission) : async () {
 if ( has_permission(pal, perm) == false ) {
 throw Error.reject( "unauthorized" );
 }
 };
 // Assign a new role to a principal
 public shared({ caller }) func assign_role( assignee: Principal, new_role: ?Role ) : async () {
 await require_permission( caller, #assign_role );
 switch new_role {
 case (?#owner) {
 throw Error.reject( "Cannot assign anyone to be the owner" );
 };
 case (_) {};
 };
 if (assignee == initializer) {
 throw Error.reject( "Cannot assign a role to the canister owner" );
 };
 roles := AssocList.replace<Principal, Role>(roles, assignee, principal_eq, new_role).0;
 role_requests := AssocList.replace<Principal, Role>(role_requests, assignee, principal_eq, null).0;
 };
 public shared({ caller }) func request_role( role: Role ) : async Principal {
 role_requests := AssocList.replace<Principal, Role>(role_requests, caller, principal_eq, ?role).0;
 return caller;
 };
 // Return the principal of the message caller/user identity
 public shared({ caller }) func callerPrincipal() : async Principal {
 return caller;
 };
 // Return the role of the message caller/user identity
 public shared({ caller }) func my_role() : async ?Role {
 return get_role(caller);
 };
 public shared({ caller }) func my_role_request() : async ?Role {
 AssocList.find<Principal, Role>(role_requests, caller, principal_eq);
 };
 public shared({ caller }) func get_role_requests() : async List.List<(Principal,Role)> {
 await require_permission( caller, #assign_role );
 return role_requests;
 };
 public shared({ caller }) func get_roles() : async List.List<(Principal,Role)> {
 await require_permission( caller, #assign_role );
 return roles;
 };
};
```

让我们看一下该程序的一些关键要素：

* 您可能会注意到greet函数是您在先前教程中看到的greet函数的变体。

但是，在此程序中，greet函数使用消息调用方来确定应应用的权限，并基于与调用方相关联的权限来确定要显示的问候。

* 该程序定义了两种自定义类型-一种用于Role，一种用于Permissions。
* Assign\_roles函数使消息调用者可以将角色分配给与身份关联的主体。
* 使用callerPrincipal函数，您可以返回与身份关联的主体。
* 使用my\_role函数可以返回与身份关联的角色。

    3. 保存并关闭main.mo文件

