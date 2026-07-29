# Create a todo
curl -X POST http://localhost:8080/api/todos \
  -H "Content-Type: application/json" \
  -d '{\n    "title": "Learn Spring"\n    "priority": "HIGH"\n  }'\n\n# Get all todos\ncurl http://localhost:8080/api/todos\n\n# Get statistics\ncurl http://localhost:8080/api/todos/stats\n```

### **3. Access H2 Console**
- Navigate to: `http://localhost:8080/h2-console`
- JDBC URL: `jdbc:h2:mem:tododb`
- Username: `sa`
- Password: (leave blank)

---

## 📊 REST API Endpoints

| Method | Endpoint | Purpose |
|--------|----------|---------|
| **GET** | `/api/todos` | Get all todos |
| **GET** | `/api/todos/{id}` | Get specific todo |
| **GET** | `/api/todos/completed/all` | Get completed todos |
| **GET** | `/api/todos/incomplete/all` | Get incomplete todos |
| **GET** | `/api/todos/category/{cat}` | Filter by category |
| **GET** | `/api/todos/priority/{pri}` | Filter by priority |
| **GET** | `/api/todos/search?term=x` | Search by title |
| **GET** | `/api/todos/stats` | Statistics |
| **GET** | `/api/todos/storage/info` | Storage info |
| **POST** | `/api/todos` | Create todo |
| **POST** | `/api/todos/export` | Export to JSON |
| **PUT** | `/api/todos/{id}` | Update todo |
| **PUT** | `/api/todos/{id}/complete` | Mark completed |
| **PUT** | `/api/todos/{id}/incomplete` | Mark incomplete |
| **DELETE** | `/api/todos/{id}` | Delete todo |
| **DELETE** | `/api/todos/completed/all` | Delete all completed |

---

## 💡 Key Spring Concepts Demonstrated

✅ **@SpringBootApplication** - Main entry point with auto-configuration
✅ **@ComponentScan** - Automatic component discovery  
✅ **@Component** - Generic Spring-managed component (FileSystemStorage)
✅ **@Service** - Business logic layer (TodoService)
✅ **@Repository** - Data access layer (TodoRepository)
✅ **@RestController** - HTTP request handlers (TodoController)
✅ **Dependency Injection** - Constructor-based bean wiring
✅ **Spring Data JPA** - Automatic CRUD operations
✅ **@Transactional** - Transaction management
✅ **File System Abstraction** - Local storage with DataSize

---

This is a **production-ready application** you can run immediately! 🎉