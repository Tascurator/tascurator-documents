# Domain model

```mermaid
classDiagram
    class Owner {
        OwnerId ownerId
        String email
        String password
        List [ShareHouse]
    }

    class OwnerId {
        String id
    }

    class ShareHouse {
        ShareHouseId shareHouseId
        String name
        Int rotationCycle
        AssignmentSheet assignmentSheet
        List [Category]
        List [Tenant]
    }

    class ShareHouseId {
        String id
    }

    class AssignmentSheet {
        Date startDate
        Date endDate
        List [TenantsWork]
    }

    class Category {
        CategoryId categoryId
        String name
        TenantId initialTenantId
        List [Task]
    }

    class CategoryId {
        String id
    }

    class Task {
        TaskId taskId
        String title
        String description
    }

    class TaskId {
        String id
    }

    class Tenant {
        TenantId tenantId
        String email
        String name
    }

    class TenantId {
        String id
    }

    class TenantsWork {
        TenantId tenantId
        List [AssignedCategory]
    }

    class AssignedCategory {
        CategoryId categoryId
        String name
        List [AssignedTask]
    }

    class AssignedTask {
        TaskId taskId
        String title
        String description
        boolean completed
    }

    Owner "1" *-- "1" OwnerId
    Owner "1" *-- "many" ShareHouse
    ShareHouse "1" *-- "1" ShareHouseId
    ShareHouse "1" *-- "many" Category
    ShareHouse "1" *-- "many" Tenant
    ShareHouse "1" *-- "1" AssignmentSheet
    Category "1" *-- "1" CategoryId
    Category "1" *-- "many" Task
    Task "1" *-- "1" TaskId
    Tenant "1" *-- "1" TenantId
    AssignmentSheet "1" *-- "many" TenantsWork
    TenantsWork "1" *-- "1" AssignedCategory
    TenantsWork "1" *-- "1" TenantId
    AssignedCategory "1" *-- "1" CategoryId
    AssignedCategory "1" *-- "many" AssignedTask
    AssignedTask "1" *-- "1" TaskId

```

# Terms and Constraints

## Owner - オーナー

## ShareHouse - シェアハウス

## Category - カテゴリー

## Task - タスク

## Tenant - テナント

## AssignmentSheet - 分担票

## TenantsWork - 割当

TenantsWork refers to the set of tasks assigned(AssignedCategory) to each tenant.

### Tenant IDs

The TenantsWork contains Tenants. The TenantsWork class has Tenant ID.

Constraints:

- The TenantsWork cannot exist without any Tenants.

### AssignedCategory

The TenantsWork contains AssignedCategory. The TenantsWork class has AssignedCategory list.

Constraints:

- The TenantsWork cannot exist without any AssignedCategory.

## AssignedCategory -　

## AssignedTask -
