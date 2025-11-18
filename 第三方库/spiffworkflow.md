# spiffworkflow


## 基础介绍


`pip install spiffworkflow`


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
            BpmnParser:
                BpmnParser: # bpmn文件解析
                    add_bpmn_file(): # 加载 BPMN 文件
                    get_spec(): # 获取流程定义
    specs: # 流程定义
        WorkflowSpec: # 流程定义
    task: # 任务
        Task: # 任务实例
            id:
            state: # 
            task_spec: # 任务定义
                name:
            complete(): # 完成任务
        TaskState: # 任务状态
            READY:
    Workflow: # 工作流程（传入定义spec）
        get_tasks(): # 获取任务列表
        is_completed(): # 查询流程是否结束
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