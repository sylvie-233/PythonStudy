# aspscheduler


## 基础介绍

定时任务
- scheduler: 任务调度器
- executor: 任务执行器
- jobstore: 任务存储器
- trigger: 任务触发器

## 核心内容
```yaml
aspscheduler:
    executors: # 执行器
        pool:
            ThreadPoolExecutor:
    jobstores: # 存储器
        sqlalchemy: 
            SQLAlchemyJobStore:
    schedulers: # 调度器
        background:
            BlockingScheduler:
                executors:
                jobstores:
                add_job():
                start():
    triggers: # 触发器
        cron: # CRON
            CronTrigger:
        date: # 日期
            DateTrigger:
        interval: # 间隔
            IntervalTrigger:
```