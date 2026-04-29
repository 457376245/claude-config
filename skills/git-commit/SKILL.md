---
name: git-commit
description: Generate conventional commit messages in Chinese for Java projects. Use when user says "commit", "create commit", "commit changes", or after completing code changes that need to be committed.
---

# Git Commit Message Skill

Generate conventional, informative Chinese commit messages for Java projects.

## When to Use
- After making code changes
- User says "commit this" / "commit changes" / "create commit"
- Before creating PRs

## Format Standard

Use Conventional Commits format:
```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types (Java context)
- **feat**: New feature (new API, new functionality)
- **fix**: Bug fix
- **refactor**: Code refactoring (no functional change)
- **test**: Add/update tests
- **docs**: Documentation only
- **perf**: Performance improvement
- **build**: Maven/Gradle changes
- **chore**: Maintenance (dependency updates, etc)

### Scope Examples (Java specific)
- Module name: `core`, `api`, `plugin-loader`
- Component: `PluginManager`, `ExtensionFactory`
- Area: `lifecycle`, `dependencies`, `security`

### Subject Rules
- Use Chinese in the subject; keep the Conventional Commit prefix (`type(scope):`) in English
- Use imperative wording in Chinese, such as `新增`, `修复`, `重构`
- Do not end the subject with punctuation
- Keep the subject concise and preferably within 50 characters
- Lowercase after type

### Body (optional but recommended)
- Write the body in Chinese
- Explain WHAT and WHY, not HOW
- Wrap at 72 chars when possible
- Reference issues in English footer style when needed, such as `Fixes #123` or `Relates to #456`

## Examples

### Simple fix
```
fix(plugin-loader): 修复插件目录缺失时的空指针

在初始化前补充空值判断，避免目录缺失时抛出
NullPointerException。

Fixes #234
```

### Feature with breaking change
```
feat(api): 新增插件依赖版本校验

BREAKING CHANGE: PluginDescriptor 现在要求使用语义化版本
格式（x.y.z），不再接受自由格式版本号。

Closes #567
```

### Refactoring
```
refactor(core): 抽取插件校验逻辑

将校验逻辑从 PluginManager 提取到独立的
PluginValidator，提升可测试性和职责清晰度。
```

### Test addition
```
test(plugin-loader): 补充插件加载集成测试

补充目录加载、JAR 加载和异常处理等场景，
确保插件加载流程可回归验证。
```

### Build/dependency update
```
build(deps): 升级 Spring Boot 到 3.2.1

升级 Spring Boot 以获取安全修复和性能改进，
当前使用方式无需额外 API 适配。
```

## Workflow

1. **Analyze changes** using `git diff --staged`
2. **Identify scope** from modified files
3. **Determine type** based on change nature
4. **Generate a Chinese message** following format
5. **Execute commit**: `git commit -m "message"`

## Token Optimization

- Read staged changes ONCE: `git diff --staged --stat` + targeted file diffs
- Don't read entire files unless necessary
- Use concise body - aim for 2-3 lines max
- Batch multiple small changes into logical commits

## Anti-patterns

鉂?Avoid:
- "fix stuff" / "update code" / "changes"
- "WIP" commits (unless explicitly requested)
- Mixing unrelated changes (use separate commits)
- Over-detailed technical implementation in message

鉁?Good commits:
- Single logical change
- Clear, searchable subject
- References issues when applicable
- Explains business value

## Integration with GitHub

After commit, suggest next steps:
- "Push changes?" 
- "Create PR for issue #X?"
- "Continue with next task?"

## Common Patterns for Java Projects

### Adding new functionality
```
feat(extension): 新增扩展优先级支持

允许扩展声明执行优先级，优先级更高的扩展先执行。

Closes #123
```

### Fixing bugs
```
fix(classloader): 修复嵌套 JAR 资源查找失败

修复插件 JAR 加载后资源查找链路不完整的问题，
避免 ClassLoader.getResource() 在嵌套 JAR 场景失效。

Fixes #456
```

### Dependency updates
```
build(deps): 升级 slf4j 到 2.0.9

升级到最新稳定版本，当前仅使用稳定 API，
无需额外兼容性改造。
```

### Documentation improvements
```
docs(readme): 新增插件开发快速开始指南

补充项目初始化、Plugin 接口实现和构建测试步骤，
帮助开发者快速上手插件开发。
```

### Performance optimizations
```
perf(plugin-loader): 缓存插件描述信息

缓存解析后的插件描述，减少重复 I/O 和解析开销，
插件加载耗时约下降 40%。

Related to #789
```

## Multi-file Changes

When changes span multiple components:

```
refactor(core): 重组插件生命周期管理

- 抽取生命周期状态机到独立类
- 将校验逻辑迁移到 validators 包
- 同步更新测试以匹配新结构

本次重构提升了可测试性和职责划分，
不改变对外 API。

Related to #111, #222
```

## Breaking Changes

Always use BREAKING CHANGE footer:

```
feat(api)!: 将 Plugin.start() 替换为 Plugin.initialize()

BREAKING CHANGE: Plugin.start() 已重命名为
Plugin.initialize()，所有插件实现都必须同步修改。

Migration guide: 将所有插件实现中的 @Override start()
替换为 @Override initialize()。

Closes #999
```

## Quick Reference Card

| Change Type | Type | Example Scope |
|-------------|------|---------------|
| New feature | feat | api, core, loader |
| Bug fix | fix | plugin-loader, lifecycle |
| Refactoring | refactor | core, utils |
| Tests | test | integration, unit |
| Docs | docs | readme, javadoc |
| Build | build | maven, deps |
| Performance | perf | classloader, cache |
| Maintenance | chore | ci, tooling |

## References

- [Conventional Commits Specification](https://www.conventionalcommits.org/)