# EventSphere — Event Management & Ticket Reservation System

> **Angular 17 · TypeScript · Angular Material · RxJS**

---

## 🚀 Setup Guide (3 Steps)

### Step 1 — Install dependencies
```bash
npm install
```

### Step 2 — Start the app
```bash
ng serve
# Open → http://localhost:4200
```

> **No JSON Server needed!** The app uses `src/assets/db.json` as a static mock backend.
> If you want a live REST API, run in a second terminal:
> ```bash
> npm run mock-api
> # Starts json-server on http://localhost:3000
> ```

---

## ❌ Fixes Applied (Errors You May Have Seen)

| Error | Fix Applied |
|-------|-------------|
| `Configuration 'development' is not set` | Added `development` + `production` config blocks to `angular.json` |
| `json-server` not recognized | `json-server` added as `devDependency`; use `npm run mock-api` or `npx json-server` |
| `npm warn deprecated` packages | Updated all Angular deps to `^17.3.0`, ts to `~5.4.0` |
| Asset path errors | Fixed `assets` config in `angular.json` to use glob format |
| Missing `environment.prod.ts` | Added `src/environments/environment.prod.ts` |

---

## 📁 Project Structure

```
eventsphere/
├── src/
│   ├── app/
│   │   ├── components/
│   │   │   ├── navbar/              # Navigation + Auth modal (template-driven)
│   │   │   ├── event-list/          # Home & events grid with filters + search
│   │   │   ├── event-detail/        # Full event info + booking card
│   │   │   ├── booking-form/        # Ticket form (Reactive Forms + validation)
│   │   │   ├── user-dashboard/      # Booking history & stats (AuthGuard)
│   │   │   └── contact/             # Contact form (template-driven)
│   │   ├── services/
│   │   │   ├── event.service.ts     # HttpClient + RxJS + in-memory cache
│   │   │   ├── booking.service.ts   # Booking CRUD + localStorage
│   │   │   └── user.service.ts      # Auth state (BehaviorSubject)
│   │   ├── models/
│   │   │   ├── event.model.ts       # Event interface + EventModel class
│   │   │   ├── booking.model.ts     # Booking interface + BookingModel class
│   │   │   └── user.model.ts        # User interface + UserModel class
│   │   ├── guards/
│   │   │   └── auth.guard.ts        # CanActivate — protects /dashboard, /book/:id
│   │   ├── interceptors/
│   │   │   └── loading.interceptor.ts  # HTTP_INTERCEPTORS + LoadingService
│   │   ├── pipes/
│   │   │   └── custom.pipes.ts      # 5 custom pipes
│   │   ├── app-routing.module.ts
│   │   ├── app.module.ts
│   │   └── app.component.*
│   ├── assets/
│   │   └── db.json                  # Static mock data (8 events)
│   ├── environments/
│   │   ├── environment.ts           # Development
│   │   └── environment.prod.ts      # Production
│   ├── styles.scss
│   └── index.html
├── angular.json
├── package.json
└── tsconfig.json
```

---

## 🛣️ Routes

| Path         | Component             | Guard      |
|--------------|-----------------------|------------|
| `/`          | → redirect `/home`    |            |
| `/home`      | EventListComponent    |            |
| `/events`    | EventListComponent    |            |
| `/event/:id` | EventDetailComponent  |            |
| `/book/:id`  | BookingFormComponent  | AuthGuard  |
| `/dashboard` | UserDashboardComponent| AuthGuard  |

---

## ✅ Angular Features Covered

- **Components** — `*ngIf`, `*ngFor`, `[ngClass]`, `[ngStyle]`, event binding
- **Routing** — route params, `routerLink`, `routerLinkActive`, `CanActivate` guard
- **Reactive Forms** — `FormBuilder`, `Validators`, custom error messages
- **Template-driven Forms** — `ngModel`, `NgForm`, `#ref` variables
- **Services & DI** — `EventService`, `BookingService`, `UserService`
- **RxJS** — `BehaviorSubject`, `switchMap`, `combineLatest`, `debounceTime`, `takeUntil`
- **Custom Pipes** — `rupees`, `availability`, `categoryFilter`, `searchFilter`, `timeSince`
- **Built-in Pipes** — `DatePipe`, `CurrencyPipe`, `TitleCasePipe`, `SlicePipe`
- **HTTP Interceptors** — `LoadingInterceptor` with `finalize` + error handling
- **Angular Material** — `MatSnackBar`, `MatSpinner`, `MatProgressBar`, `MatChips`, `MatTooltip`

---

## 🔐 Auth (Demo Mode)
- Login: any valid email + 6+ character password
- Register: fill all fields
- State persisted in `localStorage` via `BehaviorSubject`
