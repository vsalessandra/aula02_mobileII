# ARCH — Refatoração feature-first

## Estrutura final

```txt
lib/
	app/
		app_root.dart
	core/
		errors/
			app_error.dart
	features/
		todos/
			data/
				datasources/
					todo_remote_datasource.dart
					todo_local_datasource.dart
				models/
					todo_model.dart
				repositories/
					todo_repository_impl.dart
			domain/
				entities/
					todo.dart
				repositories/
					todo_repository.dart
			presentation/
				pages/
					todos_page.dart
				viewmodels/
					todo_viewmodel.dart
				widgets/
					add_todo_dialog.dart
	main.dart
```

## Diagrama do fluxo

UI (`TodosPage`) -> VM (`TodoViewModel`) -> Repo (`TodoRepositoryImpl`) -> DataSources (`TodoRemoteDataSource`, `TodoLocalDataSource`)

## Justificativa da estrutura

- Organização por feature (`todos`) facilita manutenção e crescimento.
- Separação por camadas (`data`, `domain`, `presentation`) reduz acoplamento.
- `core` concentra itens compartilháveis do app.

## Decisões de responsabilidade

- UI não chama HTTP nem SharedPreferences diretamente.
- ViewModel não conhece Widgets/BuildContext, apenas estado e ações.
- Repository centraliza acesso e escolha entre remoto/local.
- DataSources fazem integração técnica (HTTP e persistência local).
- `domain` mantém entidade e contrato do repositório.
