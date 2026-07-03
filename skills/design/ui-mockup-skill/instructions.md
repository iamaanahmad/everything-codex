# UI Mockup Skill

## Purpose
Rapidly create UI mockups, wireframes, and interactive prototypes from text descriptions as React + Tailwind components.

## Process

### 1. Understand the Screen
- What is the user trying to accomplish?
- What data is displayed?
- What actions are available?
- What is the layout (dashboard, form, list, detail)?

### 2. Choose Fidelity Level
- **Wireframe** — grayscale, boxes, placeholder text
- **Low-fi mockup** — basic colors, real labels, no polish
- **High-fi mockup** — production-ready styling, interactions

### 3. Generate Component

## Output Templates

### Dashboard Layout
```jsx
export default function Dashboard() {
  return (
    <div className="min-h-screen bg-gray-50">
      {/* Sidebar */}
      <aside className="fixed inset-y-0 left-0 w-64 bg-white border-r border-gray-200">
        <div className="p-6 font-bold text-lg">MyApp</div>
        <nav className="px-4 space-y-1">
          {["Overview", "Analytics", "Users", "Settings"].map(item => (
            <a key={item} href="#"
              className="block px-3 py-2 rounded-md text-sm text-gray-700 hover:bg-gray-100">
              {item}
            </a>
          ))}
        </nav>
      </aside>

      {/* Main */}
      <main className="ml-64 p-8">
        <h1 className="text-2xl font-bold text-gray-900 mb-6">Overview</h1>
        {/* Stat cards */}
        <div className="grid grid-cols-3 gap-6 mb-8">
          {[
            { label: "Total Users", value: "12,430" },
            { label: "Revenue", value: "$48,200" },
            { label: "Active Sessions", value: "1,024" }
          ].map(stat => (
            <div key={stat.label} className="bg-white rounded-xl p-6 shadow-sm border border-gray-100">
              <p className="text-sm text-gray-500">{stat.label}</p>
              <p className="text-3xl font-bold text-gray-900 mt-1">{stat.value}</p>
            </div>
          ))}
        </div>
      </main>
    </div>
  );
}
```

### Form Layout
```jsx
export default function LoginForm() {
  return (
    <div className="min-h-screen bg-gray-50 flex items-center justify-center">
      <div className="bg-white rounded-2xl shadow-sm border border-gray-200 p-8 w-full max-w-md">
        <h2 className="text-2xl font-bold text-gray-900 mb-6">Sign in</h2>
        <form className="space-y-4">
          <div>
            <label className="block text-sm font-medium text-gray-700 mb-1">Email</label>
            <input type="email" placeholder="you@example.com"
              className="w-full px-3 py-2 border border-gray-300 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-blue-500" />
          </div>
          <div>
            <label className="block text-sm font-medium text-gray-700 mb-1">Password</label>
            <input type="password" placeholder="••••••••"
              className="w-full px-3 py-2 border border-gray-300 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-blue-500" />
          </div>
          <button className="w-full bg-blue-600 text-white py-2 rounded-lg text-sm font-medium hover:bg-blue-700">
            Sign in
          </button>
        </form>
      </div>
    </div>
  );
}
```

### Data Table
```jsx
export default function UserTable({ users }) {
  return (
    <div className="bg-white rounded-xl border border-gray-200 overflow-hidden">
      <table className="w-full text-sm">
        <thead className="bg-gray-50 border-b border-gray-200">
          <tr>
            {["Name", "Email", "Role", "Status"].map(h => (
              <th key={h} className="px-4 py-3 text-left font-medium text-gray-500">{h}</th>
            ))}
          </tr>
        </thead>
        <tbody className="divide-y divide-gray-100">
          {users.map(user => (
            <tr key={user.id} className="hover:bg-gray-50">
              <td className="px-4 py-3 font-medium text-gray-900">{user.name}</td>
              <td className="px-4 py-3 text-gray-500">{user.email}</td>
              <td className="px-4 py-3 text-gray-500">{user.role}</td>
              <td className="px-4 py-3">
                <span className="px-2 py-1 rounded-full text-xs bg-green-100 text-green-700">
                  {user.status}
                </span>
              </td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
}
```

## Best Practices
- Use realistic placeholder data, not "Lorem ipsum"
- Always include hover/focus states
- Design mobile-first, then expand to desktop
- Use Tailwind's design system for consistent spacing and color
- Deliver as a runnable component, not a static image
