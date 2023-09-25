### set up Redux

### installation >>>

`npm install @reduxjs/toolkit react-redux`

#### created src>redux.store.ts :::

    import { configureStore } from "@reduxjs/toolkit";
    import { reducer } from "./rootReducers";

    export const store = configureStore({
    reducer
    });



    export type RootState = ReturnType<typeof store.getState>

    export type AppDispatch = typeof store.dispatch

#### created src>rooReducers.ts :::

        export const reducer = {};

#### created src>hooks.ts ::: (for TS)

    import { TypedUseSelectorHook, useDispatch, useSelector } from 'react-redux'
    import type { RootState, AppDispatch } from './store'

    // Use throughout your app instead of plain `useDispatch` and `useSelector`
    export const useAppDispatch: () => AppDispatch = useDispatch
    export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector

#### created src>lib>Providers.tsx :::

    "use client";

    import { store } from "@/redux/store";
    import React from "react";
    import { Provider } from "react-redux";


    // ! important for ant Design and Redux >>>

    const Providers = ({ children }: { children: React.ReactNode }) => {
    return (
        <Provider store={store}>

        {children}
        </Provider>
    );
    };

    export default Providers;

#### created src>app.layout.tsx :::
        <Providers>
            <html lang="en">
            <body className={inter.className}>{children}</body>
            </html>
        </Providers>

#### created src>slice>userSlice.ts :::

