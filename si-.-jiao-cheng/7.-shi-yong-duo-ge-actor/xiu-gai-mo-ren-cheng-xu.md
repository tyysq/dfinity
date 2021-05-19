# 修改默认程序



现在src目录有三个独立的目录，每个都包含main.mo模板文件。本章节中，你需要用不同的actor替换每个main.mo文件。

修改源码步骤如下

1. 打开src/assistant/main.mo文件并删除已有内容
2. 复制粘贴下面的代码

```text
import Array "mo:base/Array";
import Nat "mo:base/Nat";
// Define the actor
actor Assistant {
 stable var todos : [ToDo] = [];
 stable var nextId : Nat = 1;
// Define to-do item properties
type ToDo = {
 id: Nat;
 description: Text;
 completed: Bool;
};
 // Add to-do item utility
 func add(todos : [ToDo], desc : Text, nextId : Nat) : [ToDo] {
 let todo : ToDo = {
 id = nextId;
 description = desc;
 completed = false;
 };
 Array.append<ToDo>(todos, [todo])
};
 // Show to-do item utility
 func show(todos : [ToDo]) : Text {
 var output : Text = "\n___TO-DOs___";
 for (todo : ToDo in todos.vals()) {
 output #= "\n(" # Nat.toText(todo.id) # ") " # todo.description;
 if (todo.completed) { output #= " ✔"; };
 };
 output
 };
 public func addTodo (description : Text) : async () {
 todos := add(todos, description, nextId);
 nextId += 1;
 };
 public query func showTodos () : async Text {
 show(todos)
 };
};
```

    3. 保存并关闭main.mo文件

    4. 打开src/rock\_paper\_scissors/main.mo文件并删除已有内容

    5. 复制粘贴下面的代码

```text
import I "mo:base/Iter";
actor rock_paper_scissors {
 stable var alice_score: Nat = 0;
 stable var bob_score: Nat = 0;
 stable var alice_last: Choice = #scissors;
 stable var bob_last: Choice = #rock;
 type Choice = {
 #rock;
 #paper;
 #scissors;
 };
 public func contest() : async Text {
 for (i in I.range(0,99)) {
 battle_round();
 };
 var winner = "The contest was a draw";
 if (alice_score > bob_score) winner := "Alice won"
 else if (alice_score < bob_score) winner := "Bob won";
 return (winner);
 };
 func battle_round() : () {
 let a = alice(bob_last);
 let b = bob(alice_last);
 switch (a,b) {
 case (#rock,#scissors) alice_score +=1;
 case (#rock,#paper) bob_score +=1;
 case (#paper,#scissors) alice_score +=1;
 case (#paper,#rock) bob_score +=1;
 case (#scissors,#paper) alice_score +=1;
 case (#scissors,#rock) bob_score +=1;
 case (#rock,#rock) alice_score +=0;
 case (#paper,#paper) bob_score +=0;
 case (#scissors,#scissors) alice_score +=0;
 };
 alice_last := a;
 bob_last := b;
 return ();
};
 // Hard-coded players and choices
 func bob(last: Choice) : Choice {
 return #paper;
 };
 func alice(last: Choice) : Choice {
 return #rock;
 };
};
```

    6. 保存并关闭main.mo文件

    7. 打开src/daemon/main.mo文件并删除已有内容

    8. 复制粘贴下面的代码

```text
actor daemon {
    stable var running = false;


    public func launch(): async Text {
        running :=  true;
        debug_show "The daemon process is running";
    };


    public func stop(): async Text {
        running := false;
        debug_show "The daemon is stopped";
    };
}
```

    9. 保存并关闭main.mo文件

