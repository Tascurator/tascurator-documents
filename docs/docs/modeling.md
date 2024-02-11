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
        AssignedCategory assignedCategory
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

The Landlord can register a ShareHouse which they own.

### ShareHouse ID (Identifier)

The ShareHouse ID is the UUID.

### ShareHouse Name

The ShareHouse has a default name when created without specifying one.

Constraints：

- Uniqueness
- Greater than or equal to 1 character
- Less than or equal to 15 characters
- Can be modified by Landlord as they like
- Uppercase and lowercase letters are recognized as the same characters

### rotationCycle

The rotationCycle must be set to Weekly or Fortnightly.

Constraints：

- Cannot be assigned to a Category until the rotationCycle is set.

### assignmentSheet

The assignmentSheet is the tenant's task assignment table.

### List[Category]

The ShareHouse contains Category. The ShareHouse has Category list.

### List[Tenant]

The ShareHouse contains Tenant. The ShareHouse has Tenant list.

## Category - カテゴリー

## Task - タスク

## Tenant - テナント

## AssignmentSheet - 分担票

### startDate

### endDate:

### TenantsWork

## TenantsWork -

## AssignedCategory -　

## AssignedTask -
