# Support Module Implementation TODO

## Plan Breakdown (Approved)

### Phase 1: Core Module Structure [ ]

- [ ] Create `backend/src/support/support.module.ts`
- [ ] Create entities: `support-ticket.entity.ts`, `ticket-message.entity.ts`
- [ ] Create DTOs: `create-ticket.dto.ts`, `add-message.dto.ts`, `ticket-response.dto.ts`, `admin-ticket-query.dto.ts`, `update-ticket.dto.ts`
- [ ] Create `support.controller.ts` (user endpoints)
- [ ] Create `support-admin.controller.ts` (admin endpoints)

### Phase 2: Services & Logic [ ]

- [ ] Create `support.service.ts` (CRUD, priority logic, notifications)
- [ ] Create `support.processor.ts` (BullMQ escalation cron)
- [ ] Update `queue.constants.ts` - add 'support-jobs'

### Phase 3: Integration & Migration [ ]

- [ ] Create migration for support tables
- [ ] Update `app.module.ts` - import SupportModule
- [ ] Run migration

### Phase 4: Testing & Validation [ ]

- [ ] Create `support.service.spec.ts`
- [ ] Test endpoints manually
- [ ] Verify cron/escalation
- [ ] Mark complete

**Current Progress: Starting Phase 1**
