# A05 - Security Misconfiguration
This project provide the solution to **avoid source code exposure during the exception**. Which means it will NOT display the stack trace information. It will provide the generic error message.

## Program.cs

> A05 - Security Misconfiguration - Avoid revealing the stack trace. Below code will throw the generic error message to the user. It will NOT display any sensetive infromation

    app.UseExceptionHandler(exceptionHandlerApp =>
    {
        exceptionHandlerApp.Run(async context =>
        {
            context.Response.StatusCode = StatusCodes.Status500InternalServerError;

            
            context.Response.ContentType = Text.Plain;

            var exceptionHandlerPathFeature =
                context.Features.Get<IExceptionHandlerPathFeature>();

            await context.Response.WriteAsync("Something went wrong, please contact system administrator.");
        });
    });
