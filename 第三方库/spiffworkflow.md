# spiffworkflow


## 基础介绍


`pip install SpiffWorkflow[bpmn]`


核心概念：
- Spec（流程定义）：BPMN 文件定义的流程规则
- Workflow（工作流实例）：运行中的流程实例
- Task（任务）：流程中的一个节点（人工任务、服务任务、网关等）
- Token：流程执行的上下文，保存数据 


## 核心内容
```yaml
SpiffWorkflow:
    bpmn:
        parser:
            BpmnParser: # 解析 BPMN 文件
                parse_bpmn(): # 
        workflow:
            BpmnWorkflow: # BPMN 工作流实例
    workflow: # 
        Task: # 任务实例（运行态，包含任务状态、数据等）
            data: # 任务数据
        TaskState: # 任务的状态
        Workflow: # 工作流实例
            complete_task_from_id():
            do_engine_steps(): # 任务前进
            get_ready_user_tasks():
            get_task_from_id():
            get_tasks(): # 获取所有任务
            is_completed():
    specs:
        ExclusiveChoice:
        Parallel:
        ServiceTask:
        SubWorkflow:
        TaskSpec: # 任务定义
            name:
            ---
            connect(): # 连接任务
        UserTask:
        WorkflowSpec: # 工作流定义
            name:
            ---
            create_workflow(): # 创建工作流
    storage:
        JSONSerializer:
        WorkflowSerializer:
```


### Workflow


### Task

#### Gateways

网关
BPMN 中的分支、并行控制

#### SubProcess

子流程
复杂流程拆分


#### Timer Event

定时事件
延时/定时任务


#### Service Task

服务任务
可自动执行的任务


### Token