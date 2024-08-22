# Terms

## Landlord

- `Landlord` represents the owner of a `shareHouse` in the system. The `landlord` is responsible for managing the `shareHouse`, including setting tasks and overseeing the general operations of the property.
- The `landlord` uses the system to manage `shareHouse` and assign `tasks` to tenants.

## ShareHouse

- `ShareHouse` represents a shared residential property owned by a `landlord`.

## Category

- `Category` represents a classification or group of tasks within a `shareHouse`.
- Kitchen, Bathroom, and Living Room are set by default. `Landlords` can create and delete `categories` as needed.

## Task

- `Task` represents a specific work or activity that `tenants` are responsible for performing within a `shareHouse`. `Tasks` are assigned to `categories` to help organize and manage responsibilities.

## Tenant

- `Tenant` represents a person who resides in a `shareHouse` and is responsible for carrying out assigned tasks. `Tenants` are associated with specific `shareHouse` and can have various responsibilities within the house.

## RotationAssignment

- `RotationAssignment` represents the structure and schedule of tasks that are rotated among `tenants` in a `shareHouse`. It ensures that the distribution of chores is managed fairly and systematically over a specified cycle.

## TenantPlaceholder

- `TenantPlaceholder` represents a position within a `rotationAssignment`, indicating which tenant occupies that position. This helps in determining which `tenant` is assigned specific tasks within a `sharedHouse`.
